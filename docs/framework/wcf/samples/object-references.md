---
title: Odkazy na objekty
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 2a2da82d913d43aa9bc3ccfeb9f1f1eda12b0562
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008056"
---
# <a name="object-references"></a>Odkazy na objekty
Tento příklad ukazuje, jak předat objekty podle odkazů mezi serverem a klientem. Ukázka používá simulované *sociálních sítí*. Sociální síť se skládá z `Person` třídu, která obsahuje seznam přátel, ve kterých každý typu friend je instance `Person` třídy s vlastním seznamu přátel. Tím se vytvoří graf objektů. Služba zpřístupňuje operace v těchto sociálních sítích.  
  
 V této ukázce služba je hostována v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 `Person` Třída nemá <xref:System.Runtime.Serialization.DataContractAttribute> atribut, pomocí <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> nastaveno na `true` deklarovat jako typ odkazu. Mají všechny vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.  
  
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
  
 `GetPeopleInNetwork` Operace přebírá parametr typu `Person` a vrátí všechny uživatele v síti; to znamená, že všichni uživatelé ve `friends` seznamu vašeho přítele přátel a tak dále, aniž by duplicitní položky.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` Operace přebírá parametr typu `Person` a vrátí všechny přátele v seznamu, kteří mají také tuto osobu v jejich `friends` seznamu.  
  
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
  
 `GetCommonFriends` Operace přebírá seznam typů `Person`. Seznam by měl mít dvě `Person` objektů v ní. Operace vrátí seznam hodnot `Person` objekty, které jsou v `friends` oba seznamy `Person` objekty ve vstupním seznamu.  
  
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
 Klient proxy je vytvořený pomocí **přidat odkaz na službu** funkce sady Visual Studio.  
  
 Sociální sítě, která se skládá z pěti `Person` vytvořeny objekty. Klient každé ze tří metod volá ve službě.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Interoperabilní odkazy na objekty](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
