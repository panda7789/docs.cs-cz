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
# <a name="object-references"></a>Odkazy na objekty
Tato ukázka předvádí, jak předat objekty pomocí odkazů mezi serverem a klientem. Ukázka používá simulované *sociální sítě*. Sociální síť se skládá z `Person` třídy, která obsahuje seznam přátel, ve kterých je každý přítel instancí `Person` třídy s vlastním seznamem přátel. Tím se vytvoří graf objektů. Služba zveřejňuje operace v těchto sociálních sítích.  
  
 V této ukázce je služba hostovaná službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="service"></a>Service  
 Třída `Person` má použit atribut <xref:System.Runtime.Serialization.DataContractAttribute>, s polem <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> nastaveným na `true` pro deklaraci jako typ odkazu. U všech vlastností je použit atribut <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
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
  
 Operace `GetPeopleInNetwork` přebírá parametr typu `Person` a vrátí všechny lidi v síti. To znamená, že všichni lidé v seznamu `friends`, přátelé přítele a tak dále, bez duplicit.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operace `GetMutualFriends` přebírá parametr typu `Person` a vrátí všechny přátele ze seznamu, kteří mají tuto osobu také v seznamu `friends`.  
  
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
  
 Operace `GetCommonFriends` přebírá seznam typů `Person`. V seznamu se očekává, že budou mít dva `Person` objekty. Tato operace vrátí seznam `Person` objektů, které jsou v `friends`ch seznamech `Person` objektů ve vstupním seznamu.  
  
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
  
## <a name="client"></a>Klient  
 Klientský proxy server se vytvoří pomocí funkce **Přidat odkaz na službu** sady Visual Studio.  
  
 Vytvoří se sociální síť, která se skládá z pěti objektů `Person`. Klient volá každou ze tří metod služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Interoperabilní odkazy na objekty](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
