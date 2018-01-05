---
title: "Náhrada kontraktu dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f14b69cba50839f3c4105b286af4de0523385b38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datacontract-surrogate"></a>Náhrada kontraktu dat
Tento příklad znázorňuje, jak procesy, jako jsou serializace, deserializace, schéma export a import schématu lze přizpůsobit pomocí kontraktu dat náhradního třídy. Tento příklad ukazuje způsob použití náhradní ve scénáři klient a server, kde je dat serializovat a přenesené mezi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka používá následující kontrakt služby:  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 `AddEmployee` Operace umožňuje uživatelům přidat data o Noví zaměstnanci a `GetEmployee` operace podporuje vyhledávání pro zaměstnance na základě názvu.  
  
 Tyto operace použijte následující datový typ:  
  
```  
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 V `Employee` typu, `Person` nemůže serializovat – třída (zobrazené v následující ukázka kódu) <xref:System.Runtime.Serialization.DataContractSerializer> protože není třídou kontraktu platná data.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Můžete použít `DataContract` atribut `Person` třídy, ale to není možné. Například `Person` třídy lze definovat v samostatném sestavení, přes který nemáte žádnou kontrolu.  
  
 Zadané toto omezení, jeden ze způsobů, jak serializovat `Person` třída je nahradit pomocí jiné třídy, která je označena `DataContractAttribute` a zkopírujte přes data potřebná k nové třídě. Cílem je, aby `Person` třída zobrazí jako kontraktu k <xref:System.Runtime.Serialization.DataContractSerializer>. Všimněte si, že se jedná o jeden způsob, jak serializovat bez dat kontrakt třídy.  
  
 Ukázka logicky nahrazuje `Person` třídy s jinou třídu s názvem `PersonSurrogated`.  
  
```  
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 Náhradní kontraktu dat se používá k dosažení této nahrazení. Náhradní kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. V této ukázce `AllowNonSerializableTypesSurrogate` třída implementuje toto rozhraní.  
  
 V implementaci rozhraní je první úlohou Vytvořit mapování z typu `Person` k `PersonSurrogated`. Používá se během serializace i v době exportu schématu. Toto mapování se dosahuje implementace <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metoda.  
  
```  
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Metoda mapy `Person` instance k `PersonSurrogated` instance během serializace, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda poskytuje zpětné mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
public object GetDeserializedObject(object obj,   
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 Pro mapování `PersonSurrogated` kontraktů dat ke stávající `Person` třída během importu schématu, implementuje ukázka <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> metoda, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
public Type GetReferencedTypeOnImport(string typeName,   
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 Následující vzorový kód dokončení implementace <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
```  
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,   
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,   
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 V této ukázce je náhradní povolena v ServiceModel atribut nazvaný `AllowNonSerializableTypesAttribute`. Vývojáři by bylo potřeba použít tento atribut na jejich kontrakt služby, jak je znázorněno na `IPersonnelDataService` výše kontrakt služby. Tento atribut implementuje `IContractBehavior` a nastaví náhradní na operace jeho `ApplyClientBehavior` a `ApplyDispatchBehavior` metody.  
  
 Atribut není nutné v tomto případě – používá se pro demonstrační účely v této ukázce. Uživatele můžete případně povolit náhradní přidáním ručně podobná `IContractBehavior`, `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.  
  
 `IContractBehavior` Implementace hledá operace, které používají kontraktu kontrolou, pokud mají `DataContractSerializerOperationBehavior` zaregistrován. Pokud tomu tak je, nastaví `DataContractSurrogate` vlastnost u tohoto chování. Následující vzorový kód ukazuje, jak to provést. Nastavení náhradní na toto chování operace umožňuje k serializaci a deserializaci.  
  
```  
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 Další kroky nutné přesměrováni na zařaďte náhradní pro použití při generování metadat. Jeden mechanismus k tomu je poskytnout `IWsdlExportExtension` tedy tento příklad znázorňuje. Kliknutím na Upravit `WsdlExporter` přímo.  
  
 `AllowNonSerializableTypesAttribute` Atribut implementuje `IWsdlExportExtension` a `IContractBehavior`. Rozšíření může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě. Jeho `IWsdlExportExtension.ExportContract` implementace metod povolí náhradní přidáním jeho `XsdDataContractExporter` používá při generování schématu pro kontraktu. Následující fragment kódu ukazuje, jak to udělat.  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 Při spuštění ukázky volá klienta AddEmployee následuje GetEmployee volání na kontrolu, pokud první volání bylo úspěšné. Výsledek požadavku operace GetEmployee se zobrazí v okně konzoly klienta. Operace GetEmployee musí při hledání zaměstnanec úspěšná a tisk "nalezena".  
  
> [!NOTE]
>  Tento příklad ukazuje, jak zařaďte náhradní pro serializace, deserializovat a generování metadat. Postup zařaďte náhradní pro generování kódu z metadat se nezobrazuje. Ukázka použití náhradní k připojení do generování kódu klienta najdete v sekci [vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) ukázka.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Viz také
