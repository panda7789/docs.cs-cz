---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 1aa8b1c9d135186dba9e4da75f0c7cb9297d8e5c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462282"
---
# <a name="object-references"></a><span data-ttu-id="77593-102">Odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="77593-102">Object References</span></span>
<span data-ttu-id="77593-103">Tento příklad ukazuje, jak předat objekty podle odkazů mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="77593-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="77593-104">Ukázka používá simulované *sociálních sítí*.</span><span class="sxs-lookup"><span data-stu-id="77593-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="77593-105">Sociální síť se skládá z `Person` třídu, která obsahuje seznam přátel, ve kterých každý typu friend je instance `Person` třídy s vlastním seznamu přátel.</span><span class="sxs-lookup"><span data-stu-id="77593-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="77593-106">Tím se vytvoří graf objektů.</span><span class="sxs-lookup"><span data-stu-id="77593-106">This creates a graph of objects.</span></span> <span data-ttu-id="77593-107">Služba zpřístupňuje operace v těchto sociálních sítích.</span><span class="sxs-lookup"><span data-stu-id="77593-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="77593-108">V této ukázce služba je hostována v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="77593-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77593-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="77593-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="77593-110">Služba</span><span class="sxs-lookup"><span data-stu-id="77593-110">Service</span></span>  
 <span data-ttu-id="77593-111">`Person` Třída nemá <xref:System.Runtime.Serialization.DataContractAttribute> atribut, pomocí <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> nastaveno na `true` deklarovat jako typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="77593-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="77593-112">Mají všechny vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="77593-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```  
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="77593-113">`GetPeopleInNetwork` Operace přebírá parametr typu `Person` a vrátí všechny uživatele v síti; to znamená, že všichni uživatelé ve `friends` seznamu vašeho přítele přátel a tak dále, aniž by duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="77593-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="77593-114">`GetMutualFriends` Operace přebírá parametr typu `Person` a vrátí všechny přátele v seznamu, kteří mají také tuto osobu v jejich `friends` seznamu.</span><span class="sxs-lookup"><span data-stu-id="77593-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```  
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="77593-115">`GetCommonFriends` Operace přebírá seznam typů `Person`.</span><span class="sxs-lookup"><span data-stu-id="77593-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="77593-116">Seznam by měl mít dvě `Person` objektů v ní.</span><span class="sxs-lookup"><span data-stu-id="77593-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="77593-117">Operace vrátí seznam hodnot `Person` objekty, které jsou v `friends` oba seznamy `Person` objekty ve vstupním seznamu.</span><span class="sxs-lookup"><span data-stu-id="77593-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```  
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="77593-118">Klient</span><span class="sxs-lookup"><span data-stu-id="77593-118">Client</span></span>  
 <span data-ttu-id="77593-119">Klient proxy je vytvořený pomocí **přidat odkaz na službu** funkce sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77593-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="77593-120">Sociální sítě, která se skládá z pěti `Person` vytvořeny objekty.</span><span class="sxs-lookup"><span data-stu-id="77593-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="77593-121">Klient každé ze tří metod volá ve službě.</span><span class="sxs-lookup"><span data-stu-id="77593-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="77593-122">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="77593-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="77593-123">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77593-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="77593-124">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77593-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="77593-125">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77593-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77593-126">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="77593-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="77593-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="77593-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="77593-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="77593-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77593-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="77593-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="77593-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="77593-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [<span data-ttu-id="77593-131">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="77593-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
