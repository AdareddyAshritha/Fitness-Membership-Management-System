def get_fee(plan):
    # just a simple fee list, can change prices here
    if plan == "monthly":
        return 699
    elif plan == "quarterly":
        return 1799
    elif plan == "yearly":
        return 4999
    else:
        return 0


def total_members():
    # counts how many lines are in the file 
    try:
        f = open("members.txt", "r")
    except:
        return 0

    lines = f.readlines()
    f.close()
    return len(lines)

def show_total_members():
    print("Total Members:",total_members())

def add_member():
    print("\n-- Add New Member --")
    name = input("Name: ")
    age = input("Age: ")
    plan = input("Plan (monthly/quarterly/yearly): ").lower()

    fee = get_fee(plan)
    new_id = total_members()+1

    f = open("members.txt", "a")
    f.write(str(new_id) + "," + name + "," + age + "," + plan + "," + str(fee) + "\n")
    f.close()

    print("Done! New member id is", new_id, "and fee is", fee)


def view_members():
    print("\n-- All Members --")
    try:
        f = open("members.txt", "r")
    except:
        print("no members added yet")
        return

    for line in f:
        details = line.strip().split(",")
        # details[0]=id, [1]=name, [2]=age, [3]=plan, [4]=fee
        print("ID:", details[0], " Name:", details[1], " Age:", details[2], " Plan:", details[3], " Fee:", details[4])

    f.close()


def search_member():
    key = input("\nEnter name or id to search: ")

    try:
        f = open("members.txt", "r")
    except:
        print("no members added yet")
        return

    result_found = False
    for line in f:
        details = line.strip().split(",")
        if key == details[0] or key.lower() == details[1].lower():
            print("Found -> ID:", details[0], "Name:", details[1], "Age:", details[2], "Plan:", details[3], "Fee:", details[4])
            result_found = True

    f.close()

    if result_found == False:
        print("didn't find anyone with that")


def update_member():
    id_to_update = input("\nEnter the id you want to update: ")

    f = open("members.txt", "r")
    all_lines = f.readlines()
    f.close()

    updated_lines = []
    was_found = False

    for line in all_lines:
        details = line.strip().split(",")

        if details[0] == id_to_update:
            was_found = True
            print("okay found the member:", details[1])
            new_name = input("new name: ")
            new_age = input("new age: ")
            new_plan = input("new plan (monthly/quarterly/yearly): ")
            new_fee = get_fee(new_plan)

            updated_line = id_to_update + "," + new_name + "," + new_age + "," + new_plan + "," + str(new_fee) + "\n"
            updated_lines.append(updated_line)
        else:
            updated_lines.append(line)

    f = open("members.txt", "w")
    f.writelines(updated_lines)
    f.close()

    if was_found:
        print("member updated!")
    else:
        print("couldn't find that id")


def delete_member():
    id_to_delete = input("\nEnter the id you want to delete: ")

    f = open("members.txt", "r")
    all_lines = f.readlines()
    f.close()

    remaining_lines = []
    was_found = False

    for line in all_lines:
        details = line.strip().split(",")
        if details[0] == id_to_delete:
            was_found = True
            # just skip adding this line back, basically deletes it
        else:
            remaining_lines.append(line)

    f = open("members.txt", "w")
    f.writelines(remaining_lines)
    f.close()

    if was_found:
        print("deleted that member")
    else:
        print("no member with that id")


def fee_calc_only():
    plan = input("\nwhich plan? (monthly/quarterly/yearly): ")
    fee = get_fee(plan)
    print("that plan costs:", fee)


# main program starts here
print("##### Hi,Welcome to Gym Membership #####")

while True:
    print("\n1 - Add Member")
    print("2 - View the Members")
    print("3 - Search Member")
    print("4 - Update Member")
    print("5 - Delete Member")
    print("6 - Calculate Fee")
    print("7- Total Members")
    print("8 - Quit")

    option = input("Select the options from 1 to 8 for your need:")

    if option == "1":
        add_member()
    elif option == "2":
        view_members()
    elif option == "3":
        search_member()
    elif option == "4":
        update_member()
    elif option == "5":
        delete_member()
    elif option == "6":
        fee_calc_only()
    elif option == "7":
        show_total_members()
    elif option == "8":
        print("Thank You for visting!")
        break
    else:
        print("It is  not a valid option please ,try again")