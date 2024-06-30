<script setup lang="ts">
import MainNav from '@/components/MainNav.vue'
import UserNav from '@/components/UserNav.vue'
import DateRangePicker from '@/components/DateRangePicker.vue'
import Overview from '@/components/Overview.vue'
import DataTable from '@/components/DataTable.vue'

import {
    Card,
    CardContent,
    CardDescription,
    CardHeader,
    CardTitle,
} from '@/components/ui/card'

import {
    Tabs,
    TabsContent,
    TabsList,
    TabsTrigger
} from '@/components/ui/tabs'

</script>

<template>
    <div class="md:hidden">
        <VPImage
            alt="Dashboard"
            width="1280"
            height="1214" class="block" :image="{
            dark: '/examples/dashboard-dark.png',
            light: '/examples/dashboard-light.png',
            }"
        />
    </div>
    <div class="hidden flex-col md:flex">
        <div class="border-b">
            <div class="flex h-16 items-center px-4">
                <TeamSwitcher />
                <MainNav class="mx-6" />
                <div class="ml-auto flex items-center space-x-4">
                <Search />
                <UserNav />
                </div>
            </div>
        </div>

      <!-- Content Area -->
    <div class="flex-1 space-y-4 p-8 pt-6">
        <div class="flex items-center justify-between space-y-2">
            <h2 class="text-3xl font-bold tracking-tight">
            Dashboard
            </h2>
            <div class="flex items-center space-x-2">
            <DateRangePicker />
            <Button>Download</Button>
            </div>
        </div>

        <Tabs default-value="overview" class="space-y-4">
            <TabsList>
              <TabsTrigger value="overview">
                Overview
              </TabsTrigger>
              <TabsTrigger value="analytics" disabled>
                Analytics
              </TabsTrigger>
              <TabsTrigger value="reports" disabled>
                Reports
              </TabsTrigger>
              <TabsTrigger value="notifications" disabled>
                Notifications
              </TabsTrigger>
            </TabsList>

            <!-- Plot Area -->
            <TabsContent value="overview" class="space-y-4">
                <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
                </div>
                <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
                    <Card class="col-span-4">
                      <CardHeader>
                        <CardTitle>Overview</CardTitle>
                      </CardHeader>
                      <CardContent class="pl-2">
                        <Overview />
                      </CardContent>
                    </Card>
                    <Card class="col-span-3">
                      <CardHeader>
                        <CardTitle>Recent Sales</CardTitle>
                        <CardDescription>
                          You made 265 sales this month.
                        </CardDescription>
                      </CardHeader>
                      <CardContent>
                        <RecentSales />
                      </CardContent>
                    </Card>
                </div>

                <div class="rounded-md border">
                    <DataTable  />
                </div>
            </TabsContent>
        </Tabs>
      </div>
    </div>
</template>