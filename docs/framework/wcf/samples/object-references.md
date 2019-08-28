---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: f82ebe741c2deaccb3bd6593c7b4f53a646582dd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039155"
---
# <a name="object-references"></a>Odkazy na objekty
Tato ukázka předvádí, jak předat objekty pomocí odkazů mezi serverem a klientem. Ukázka používá simulované *sociální sítě*. Sociální síť se skládá ze `Person` třídy, která obsahuje seznam přátel, ve kterých je každý přítel instancí `Person` třídy s vlastním seznamem přátel. Tím se vytvoří graf objektů. Služba zveřejňuje operace v těchto sociálních sítích.  
  
 V této ukázce je služba hostovaná službou Internetová informační služba (IIS) a klientem je Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Třída má `true` atribut použit s polem nastaveným na k deklaraci jako typ odkazu. <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `Person` <xref:System.Runtime.Serialization.DataContractAttribute> Všechny vlastnosti mají <xref:System.Runtime.Serialization.DataMemberAttribute> použit atribut.  
  
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
  
 Operace přebírá parametr typu `Person` a vrátí všechny lidi v síti, tedy `friends` všechny lidi v seznamu, přátele přítele a tak dále, bez duplicitních hodnot. `GetPeopleInNetwork`  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operace přebírá parametr typu `Person` a vrátí všechny přátele ze seznamu, kteří `friends` mají tuto osobu také v seznamu. `GetMutualFriends`  
  
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
  
 Operace přebírá seznam typů `Person`. `GetCommonFriends` V seznamu se očekává, že budou `Person` mít dva objekty. Operace vrátí seznam `Person` objektů, které jsou `friends` v seznamech obou `Person` objektů ve vstupním seznamu.  
  
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
  
 Vytvoří se sociální síť, která se `Person` skládá z pěti objektů. Klient volá každou ze tří metod služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Interoperabilní odkazy na objekty](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
