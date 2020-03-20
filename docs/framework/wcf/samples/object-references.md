---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183450"
---
# <a name="object-references"></a><span data-ttu-id="d4133-102">Odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="d4133-102">Object References</span></span>
<span data-ttu-id="d4133-103">Tato ukázka ukazuje, jak předat objekty odkazy mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="d4133-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="d4133-104">Vzorek používá simulované *sociální sítě*.</span><span class="sxs-lookup"><span data-stu-id="d4133-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="d4133-105">Sociální síť se skládá `Person` z třídy, která obsahuje seznam přátel, `Person` ve kterém každý přítel je instancí třídy, s vlastním seznamem přátel.</span><span class="sxs-lookup"><span data-stu-id="d4133-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="d4133-106">Tím se vytvoří graf objektů.</span><span class="sxs-lookup"><span data-stu-id="d4133-106">This creates a graph of objects.</span></span> <span data-ttu-id="d4133-107">Služba zveřejňuje operace na těchto sociálních sítích.</span><span class="sxs-lookup"><span data-stu-id="d4133-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="d4133-108">V této ukázce je služba hostována internetovou informační službou (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="d4133-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4133-109">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d4133-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="d4133-110">Služba</span><span class="sxs-lookup"><span data-stu-id="d4133-110">Service</span></span>  
 <span data-ttu-id="d4133-111">Třída `Person` má <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> s polem nastaveným na `true` deklarování jako typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="d4133-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="d4133-112">Všechny vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> mají atribut použit.</span><span class="sxs-lookup"><span data-stu-id="d4133-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d4133-113">Operace `GetPeopleInNetwork` přebírá parametr typu `Person` a vrátí všechny osoby v síti; to znamená, že všichni `friends` lidé v seznamu, přátelé přítele a tak dále, bez duplikátů.</span><span class="sxs-lookup"><span data-stu-id="d4133-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="d4133-114">Operace `GetMutualFriends` přebírá parametr typu `Person` a vrátí všechny přátele v seznamu, kteří `friends` mají také tuto osobu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4133-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d4133-115">Operace `GetCommonFriends` má seznam typu `Person`.</span><span class="sxs-lookup"><span data-stu-id="d4133-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="d4133-116">Očekává se, že `Person` v seznamu budou dva objekty.</span><span class="sxs-lookup"><span data-stu-id="d4133-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="d4133-117">Operace vrátí seznam `Person` objektů, které `friends` jsou v `Person` seznamech obou objektů ve vstupním seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4133-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="d4133-118">Klient</span><span class="sxs-lookup"><span data-stu-id="d4133-118">Client</span></span>  
 <span data-ttu-id="d4133-119">Proxy klienta je vytvořen pomocí funkce **Přidat odkaz na službu** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4133-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="d4133-120">Vytvoří se sociální síť, `Person` která se skládá z pěti objektů.</span><span class="sxs-lookup"><span data-stu-id="d4133-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="d4133-121">Klient volá každou ze tří metod ve službě.</span><span class="sxs-lookup"><span data-stu-id="d4133-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4133-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d4133-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d4133-123">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4133-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d4133-124">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4133-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d4133-125">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4133-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4133-126">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d4133-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4133-127">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d4133-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d4133-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d4133-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4133-129">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d4133-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="d4133-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4133-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="d4133-131">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="d4133-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
