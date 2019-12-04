---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714683"
---
# <a name="object-references"></a><span data-ttu-id="6a226-102">Odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="6a226-102">Object References</span></span>
<span data-ttu-id="6a226-103">Tato ukázka předvádí, jak předat objekty pomocí odkazů mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="6a226-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="6a226-104">Ukázka používá simulované *sociální sítě*.</span><span class="sxs-lookup"><span data-stu-id="6a226-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="6a226-105">Sociální síť se skládá z `Person` třídy, která obsahuje seznam přátel, ve kterých je každý přítel instancí `Person` třídy s vlastním seznamem přátel.</span><span class="sxs-lookup"><span data-stu-id="6a226-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="6a226-106">Tím se vytvoří graf objektů.</span><span class="sxs-lookup"><span data-stu-id="6a226-106">This creates a graph of objects.</span></span> <span data-ttu-id="6a226-107">Služba zveřejňuje operace v těchto sociálních sítích.</span><span class="sxs-lookup"><span data-stu-id="6a226-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="6a226-108">V této ukázce je služba hostovaná službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="6a226-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a226-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6a226-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="6a226-110">Service</span><span class="sxs-lookup"><span data-stu-id="6a226-110">Service</span></span>  
 <span data-ttu-id="6a226-111">Třída `Person` má použit atribut <xref:System.Runtime.Serialization.DataContractAttribute>, s polem <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> nastaveným na `true` pro deklaraci jako typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="6a226-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="6a226-112">U všech vlastností je použit atribut <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6a226-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="6a226-113">Operace `GetPeopleInNetwork` přebírá parametr typu `Person` a vrátí všechny lidi v síti. To znamená, že všichni lidé v seznamu `friends`, přátelé přítele a tak dále, bez duplicit.</span><span class="sxs-lookup"><span data-stu-id="6a226-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="6a226-114">Operace `GetMutualFriends` přebírá parametr typu `Person` a vrátí všechny přátele ze seznamu, kteří mají tuto osobu také v seznamu `friends`.</span><span class="sxs-lookup"><span data-stu-id="6a226-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="6a226-115">Operace `GetCommonFriends` přebírá seznam typů `Person`.</span><span class="sxs-lookup"><span data-stu-id="6a226-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="6a226-116">V seznamu se očekává, že budou mít dva `Person` objekty.</span><span class="sxs-lookup"><span data-stu-id="6a226-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="6a226-117">Tato operace vrátí seznam `Person` objektů, které jsou v `friends`ch seznamech `Person` objektů ve vstupním seznamu.</span><span class="sxs-lookup"><span data-stu-id="6a226-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="6a226-118">Klient</span><span class="sxs-lookup"><span data-stu-id="6a226-118">Client</span></span>  
 <span data-ttu-id="6a226-119">Klientský proxy server se vytvoří pomocí funkce **Přidat odkaz na službu** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6a226-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="6a226-120">Vytvoří se sociální síť, která se skládá z pěti objektů `Person`.</span><span class="sxs-lookup"><span data-stu-id="6a226-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="6a226-121">Klient volá každou ze tří metod služby.</span><span class="sxs-lookup"><span data-stu-id="6a226-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6a226-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="6a226-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6a226-123">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6a226-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6a226-124">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6a226-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6a226-125">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6a226-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6a226-126">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="6a226-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a226-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6a226-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6a226-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="6a226-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a226-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6a226-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="6a226-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a226-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="6a226-131">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="6a226-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
