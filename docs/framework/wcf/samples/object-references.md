---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5ac8eba44168befae92bef30a054c00d997cc54b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965602"
---
# <a name="object-references"></a><span data-ttu-id="e89b4-102">Odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="e89b4-102">Object References</span></span>
<span data-ttu-id="e89b4-103">Tato ukázka předvádí, jak předat objekty pomocí odkazů mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="e89b4-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="e89b4-104">Ukázka používá simulované *sociální sítě*.</span><span class="sxs-lookup"><span data-stu-id="e89b4-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="e89b4-105">Sociální síť se skládá ze `Person` třídy, která obsahuje seznam přátel, ve kterých je každý přítel instancí `Person` třídy s vlastním seznamem přátel.</span><span class="sxs-lookup"><span data-stu-id="e89b4-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="e89b4-106">Tím se vytvoří graf objektů.</span><span class="sxs-lookup"><span data-stu-id="e89b4-106">This creates a graph of objects.</span></span> <span data-ttu-id="e89b4-107">Služba zveřejňuje operace v těchto sociálních sítích.</span><span class="sxs-lookup"><span data-stu-id="e89b4-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="e89b4-108">V této ukázce je služba hostovaná službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="e89b4-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e89b4-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e89b4-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e89b4-110">Služba</span><span class="sxs-lookup"><span data-stu-id="e89b4-110">Service</span></span>  
 <span data-ttu-id="e89b4-111">Třída má `true` atribut použit s polem nastaveným na k deklaraci jako typ odkazu. <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `Person` <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="e89b4-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="e89b4-112">Všechny vlastnosti mají <xref:System.Runtime.Serialization.DataMemberAttribute> použit atribut.</span><span class="sxs-lookup"><span data-stu-id="e89b4-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="e89b4-113">Operace přebírá parametr typu `Person` a vrátí všechny lidi v síti, tedy `friends` všechny lidi v seznamu, přátele přítele a tak dále, bez duplicitních hodnot. `GetPeopleInNetwork`</span><span class="sxs-lookup"><span data-stu-id="e89b4-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="e89b4-114">Operace přebírá parametr typu `Person` a vrátí všechny přátele ze seznamu, kteří `friends` mají tuto osobu také v seznamu. `GetMutualFriends`</span><span class="sxs-lookup"><span data-stu-id="e89b4-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="e89b4-115">Operace přebírá seznam typů `Person`. `GetCommonFriends`</span><span class="sxs-lookup"><span data-stu-id="e89b4-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="e89b4-116">V seznamu se očekává, že budou `Person` mít dva objekty.</span><span class="sxs-lookup"><span data-stu-id="e89b4-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="e89b4-117">Operace vrátí seznam `Person` objektů, které jsou `friends` v seznamech obou `Person` objektů ve vstupním seznamu.</span><span class="sxs-lookup"><span data-stu-id="e89b4-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e89b4-118">Klient</span><span class="sxs-lookup"><span data-stu-id="e89b4-118">Client</span></span>  
 <span data-ttu-id="e89b4-119">Klientský proxy server se vytvoří pomocí funkce **Přidat odkaz na službu** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e89b4-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="e89b4-120">Vytvoří se sociální síť, která se `Person` skládá z pěti objektů.</span><span class="sxs-lookup"><span data-stu-id="e89b4-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="e89b4-121">Klient volá každou ze tří metod služby.</span><span class="sxs-lookup"><span data-stu-id="e89b4-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e89b4-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e89b4-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e89b4-123">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e89b4-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e89b4-124">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e89b4-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e89b4-125">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e89b4-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e89b4-126">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e89b4-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e89b4-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e89b4-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e89b4-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="e89b4-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e89b4-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e89b4-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="e89b4-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e89b4-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="e89b4-131">Interoperabilní odkazy na objekty</span><span class="sxs-lookup"><span data-stu-id="e89b4-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
