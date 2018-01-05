---
title: Odkazy na objekty
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86b442ffeeeb77a0c124b9b3e3441ba24d68e4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="object-references"></a>Odkazy na objekty
Tento příklad znázorňuje, jak předat objekty podle odkazů mezi serverem a klientem. Ukázka použití simulated *sociálních sítí*. Sociální sítě se skládá z `Person` třídu, která obsahuje seznam přátel, ve kterých je každý friend instance `Person` třída, s vlastní seznamu přátel. Tím se vytvoří graf objektů. Službu zpřístupní operace v těchto sociálních sítích.  
  
 V této ukázce služba je hostovaná Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 `Person` Třída má <xref:System.Runtime.Serialization.DataContractAttribute> atribut použitý, s <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> pole nastavené na `true` deklarovat jako odkazového typu. Všechny vlastnosti <xref:System.Runtime.Serialization.DataMemberAttribute> atribut použitý.  
  
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
  
 `GetPeopleInNetwork` Operace přebírá parametr typu `Person` a vrátí všechny uživatele v síti; to znamená, že všichni uživatelé ve `friends` seznamu, friend přátel a tak dále, bez duplicitní položky.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` Operace přebírá parametr typu `Person` a vrátí všechny přátel v seznamu, který také mít tato osoba v jejich `friends` seznamu.  
  
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
  
 `GetCommonFriends` Operace přebírá seznam typu `Person`. V seznamu by měl být dva `Person` objekty v něm. Operaci vrátí seznam hodnot `Person` objekty, které jsou v `friends` seznamy obou `Person` objekty ve vstupním seznamu.  
  
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
  
## <a name="client"></a>Klient  
 Proxy server klienta je vytvořený pomocí **přidat odkaz na službu** funkce [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
 Sociální sítě, která se skládá z pěti `Person` vytvořeny objekty. Klient volá všechny tři metody ve službě.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Interoperabilní odkazy na objekty](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
