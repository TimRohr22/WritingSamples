### Meta Information for Writing Sample
|  |  |
|--|--|
| **Abstract** | The first in a three-part series of articles discussing SharePoint security, focusing on how to manage access to SharePoint resources using groups. This article introduces the topic of rights inheritance and discusses how it applies to real world examples. |
| **Audience** | Professional, enterprise-wide audience of SharePoint users. |
| **Tone** | Corporate Informal |
|  |  |
# Manage Rights in SharePoint with Groups (Part I)
If you are responsible for the management of a SharePoint site, chances are you've faced a situation where you needed to safeguard a portion of the content. For instance, if there are sensitive or legally protected resources, certain precautions must be taken to ensure that only authorized personnel have access. SharePoint Groups are a powerful tool to organize these rights and privileges.

In this three-part series, we will outline recommended best practices for the management of rights on a SharePoint site utilizing groups, inheritance, and a little forethought.

## Understanding Rights Inheritance
Within a site, smaller organizational units inherit rights from larger units above them in the hierarchy. Site privileges flow to Libraries, and from there to folders and sub-folders, down to the individual objects. Someone granted, at the top level of the site, the right to view that site, can view any content on that site, no matter how many steps or sub-folders are involved. This is inheritance: rights granted at a higher level flow down to sub-resources beneath that object.

However, at any level in the hierarchy of content organization in the site, we can break inheritance and establish a new inheritance chain that will determine access from that point in the hierarchy and down. This is exactly how you could wall off content from unauthorized access. In effect, you would be saying: no matter what access someone might have had *above* this point, from here and for all sub-resources, they will need a new grant of rights.

### Preventing Data Loss
This breaking of inheritance affects even Site Administrators, so it is imperative that the granting of rights doesn't just satisfy the needs of those requiring access, but that it does so in a way that is not dependent on a single employee controlling that access. The internet is full of stories where critical data was lost not because it was deleted, but because the last admin left the organization, and no one else had been granted access.

How best to approach this problem? We're glad you asked.

## The Basic Model
Your site already has certain groups like **Site Owners**, **Members**, and **Visitors**. These basic groups generally control what content a particular visitor can see and/or alter (via inheritance). However, anywhere in our site where we need to manage a significant population of visitors or impose a significant limitation of rights, we will need to break inheritance and create groups that will manage access.

To accomplish this, we will institute a tiered model of groups. At the lowest tier, groups will represent the defined sorts of access required by your visitors. Perhaps one set of users only needs to be able to view the data, while another should have rights to update and edit the data. The next highest tier of our model will consist of a single group that *owns* (and administrates) the lower groups. With that arrangement, members of the owning group will be able to control membership and rights for the lower tier groups.

A pre-existing group (such as **Site Owners**) can be utilized as the owner, or a new group can be created should even the **Site Owners** require differentiated rights. The most important thing, here, is that lower tier groups are not owned by a single person. Instead, they should be, themselves, owned by a group. This will prevent the permanent loss of access to important data when an employee transitions out of the organization.

### The Solutions
That leaves us with two arrangements that could satisfy both our need for providing varying levels of access for different groups, and our need to limit the potential loss of data by poorly designed rights.

The first option is to put the **Site Owners** group as the top-level owner of any series of groups limiting access to those resources. For instance, if you create the group **Department Daily Use** and give it rights to view certain resources, you could designate the **Site Owners** group as its owner, allowing anyone in **Site Owners** to administer membership in the **Department Daily Use** group.

![Diagram of simple group ownership](https://raw.githubusercontent.com/TimRohr22/WritingSamples/refs/heads/main/images/sp_simple_ownership.png)

Or if there was a single **Department Admin** group responsible for the administration of various other departmental groups (including **Department Daily Use** and **Department Editors**), it could be the owner of those other groups, while having the **Site Owners** group as its owner.

![Diagram of intermediate group ownership](https://raw.githubusercontent.com/TimRohr22/WritingSamples/refs/heads/main/images/sp_intermediate_ownership.png)

The idea, here, is that a group like the **Site Owners** is the top group in the chain of ownership. This arrangement works if there is no need to limit a member of the **Site Owners** from being able to manage a resource. That is, if every member of the **Site Owners** group is authorized to view everything on a site, there is no reason why **Site Owners** couldn't own and administer other groups.

However, if there is a reason to wall off a portion of the site from even members of the **Site Owners** group (for instance, an IT&S employee in the **Site Owners** group might not be authorized to view certain HIPAA information stored on the site), then you need to do things in a slightly different way.

In this case, you would follow the pattern of having the **Department Admin** group owning the lower tier groups (**Department Daily Use** and **Department Editors**), but you would designate the **Department Admin** group to be the owner of itself. By creating this ownership structure, you will have effectively created an admin group for everything downstream of where you broke inheritance, limiting what can be seen by any site-level group.

![Diagram of group owning itself in group hierarchy](https://raw.githubusercontent.com/TimRohr22/WritingSamples/refs/heads/main/images/sp_group_owning_itself.png)

## Applying the Model - Planning
As you think about how to grant or limit rights to the data you are responsible for safeguarding, think about the different sets of people who will need access, and the different levels of access they will need. Think also about who should administer those groups, and whether you need to limit rights even to the owners of the site. Once you have a plan for what sort of groups and privileges you need to create, continue on to **Part 2** of this series, where we’ll walk through the steps involved in creating the groups you need.

