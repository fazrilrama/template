<script>
/**
 * Top-users component
 */
import simplebar from "simplebar-vue";

export default {
    data() {
        return {
            users: [{
                profile: require("@/assets/images/users/avatar-4.jpg"),
                name: "Glenn Holden",
                location: "Nevada",
                status: "Cancel",
                price: "$250.00",
            },
            {
                profile: require("@/assets/images/users/avatar-5.jpg"),
                name: "Lolita Hamill",
                location: "Texas",
                status: "Success",
                price: "$110.00",
            },
            {
                profile: require("@/assets/images/users/avatar-6.jpg"),
                name: "Robert Mercer",
                location: "California",
                status: "Active",
                price: "$420.00",
            },
            {
                profile: require("@/assets/images/users/avatar-7.jpg"),
                name: "Marie Kim",
                location: "Montana",
                status: "Pending",
                price: "$120.00",
            },
            {
                profile: require("@/assets/images/users/avatar-8.jpg"),
                name: "Sonya Henshaw",
                location: "Colorado",
                status: "Active",
                price: "$112.00",
            },
            {
                profile: require("@/assets/images/users/avatar-2.jpg"),
                name: "Marie Kim",
                location: "Australia",
                status: "Success",
                price: "$120.00",
            },
            {
                profile: require("@/assets/images/users/avatar-1.jpg"),
                name: "Sonya Henshaw",
                location: "India",
                status: "Cancel",
                price: "$112.00",
            },
            ],
        };
    },

    components: { simplebar },

};
</script>

<template>
    <BCol xl="4">
        <BCard no-body>
            <BCardBody>
                <div class="float-end">
                    <BDropdown variant="white" toggle-class="p-0" menu-class="dropdown-menu-end">
                        <template v-slot:button-content>
                            <span class="text-muted">
                                All Members
                                <i class="mdi mdi-chevron-down ms-1"></i>
                            </span>
                        </template>
                        <BDropdownItem href="#">Locations</BDropdownItem>
                        <BDropdownItem href="#">Revenue</BDropdownItem>
                        <BDropdownItem href="#">Join Date</BDropdownItem>
                    </BDropdown>
                </div>
                <h4 class="card-title mb-4">Top Users</h4>

                <simplebar style="max-height: 336px;">
                    <div class="table-responsive">
                        <BTableSimple class="table-borderless table-centered table-nowrap">
                            <BTbody>
                                <BTr v-for="(item, index) in users" :key="index">
                                    <BTd style="width: 20px;">
                                        <img :src="item.profile" class="avatar-xs rounded-circle" alt="..." />
                                    </BTd>
                                    <BTd>
                                        <h6 class="font-size-15 mb-1 fw-normal">{{ item.name }}</h6>
                                        <p class="text-muted font-size-13 mb-0">
                                            <i class="mdi mdi-map-marker"></i>
                                            {{ item.location }}
                                        </p>
                                    </BTd>
                                    <BTd>
                                        <span class="badge font-size-12" :class="{
                                            'bg-soft-success': item.status === 'Success',
                                            'bg-soft-danger': item.status === 'Cancel',
                                            'bg-soft-info': item.status === 'Active',
                                            'bg-soft-warning': item.status === 'Pending'
                                        }">{{ item.status }}</span>
                                    </BTd>
                                    <BTd class="text-muted fw-semibold text-end">
                                        <i class="icon-xs icon me-2 text-success" data-feather="trending-up"></i>
                                        {{ item.price }}
                                    </BTd>
                                </BTr>
                            </BTbody>
                        </BTableSimple>
                    </div>
                </simplebar>
            </BCardBody>
        </BCard>
    </BCol>
</template>
