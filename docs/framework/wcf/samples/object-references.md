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
# <a name="object-references"></a>Odkazy na objekty
Tato ukázka ukazuje, jak předat objekty odkazy mezi serverem a klientem. Vzorek používá simulované *sociální sítě*. Sociální síť se skládá `Person` z třídy, která obsahuje seznam přátel, `Person` ve kterém každý přítel je instancí třídy, s vlastním seznamem přátel. Tím se vytvoří graf objektů. Služba zveřejňuje operace na těchto sociálních sítích.  
  
 V této ukázce je služba hostována internetovou informační službou (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Třída `Person` má <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> s polem nastaveným na `true` deklarování jako typ odkazu. Všechny vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> mají atribut použit.  
  
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
  
 Operace `GetPeopleInNetwork` přebírá parametr typu `Person` a vrátí všechny osoby v síti; to znamená, že všichni `friends` lidé v seznamu, přátelé přítele a tak dále, bez duplikátů.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operace `GetMutualFriends` přebírá parametr typu `Person` a vrátí všechny přátele v seznamu, kteří `friends` mají také tuto osobu v seznamu.  
  
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
  
 Operace `GetCommonFriends` má seznam typu `Person`. Očekává se, že `Person` v seznamu budou dva objekty. Operace vrátí seznam `Person` objektů, které `friends` jsou v `Person` seznamech obou objektů ve vstupním seznamu.  
  
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
 Proxy klienta je vytvořen pomocí funkce **Přidat odkaz na službu** sady Visual Studio.  
  
 Vytvoří se sociální síť, `Person` která se skládá z pěti objektů. Klient volá každou ze tří metod ve službě.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Interoperabilní odkazy na objekty](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
