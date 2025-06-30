# Simple-tasks-web
import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input"; import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs"; import { DollarSign, Gift, User } from "lucide-react";

const tasks = [ { id: 1, platform: "Instagram", task: "Follow @brand", reward: 1.0 }, { id: 2, platform: "Twitter", task: "Retweet a post", reward: 0.75 }, { id: 3, platform: "YouTube", task: "Subscribe to channel", reward: 1.25 }, ];

export default function SocialTasksDashboard() { const [balance, setBalance] = useState(0); const [completedTasks, setCompletedTasks] = useState([]); const [paymentAmount, setPaymentAmount] = useState(0);

const handleCompleteTask = (task) => { if (!completedTasks.includes(task.id)) { setBalance(balance + task.reward); setCompletedTasks([...completedTasks, task.id]); } };

const handlePayment = () => { alert(Payment of $${paymentAmount} processed.); setBalance(balance - paymentAmount); setPaymentAmount(0); };

return ( <div className="p-6 max-w-4xl mx-auto"> <h1 className="text-3xl font-bold mb-4">📱 Social Media Tasks Dashboard</h1>

<Tabs defaultValue="tasks" className="w-full">
    <TabsList>
      <TabsTrigger value="tasks"><Gift className="mr-2 h-4 w-4" />Tasks</TabsTrigger>
      <TabsTrigger value="rewards"><User className="mr-2 h-4 w-4" />Rewards</TabsTrigger>
      <TabsTrigger value="payment"><DollarSign className="mr-2 h-4 w-4" />Payments</TabsTrigger>
    </TabsList>

    <TabsContent value="tasks">
      <div className="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
        {tasks.map((task) => (
          <Card key={task.id} className="p-4">
            <CardContent>
              <h2 className="text-xl font-semibold">{task.platform}</h2>
              <p className="my-2">{task.task}</p>
              <p className="text-green-600 font-bold">Earn ${task.reward.toFixed(2)}</p>
              <Button
                className=
