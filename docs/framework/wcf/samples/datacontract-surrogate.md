---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 9677e3cf024e6c1e5b2f3360423ab55536748495
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600033"
---
# <a name="datacontract-surrogate"></a>Náhrada kontraktu dat
Tato ukázka předvádí, jak lze upravit procesy jako serializace, deserializace, Export schématu a import schématu pomocí náhradní třídy kontraktu dat. V této ukázce se dozvíte, jak použít náhradu ve scénáři klienta a serveru, kde jsou data serializována a přenášena mezi klientem a službou Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka používá následující kontrakt služby:  
  
```csharp
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
  
 Tato `AddEmployee` operace umožňuje uživatelům přidávat data o nových zaměstnancích a `GetEmployee` operace podporuje hledání zaměstnanců na základě názvu.  
  
 Tyto operace používají následující datový typ:  
  
```csharp
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
  
 V typu není možné `Employee` `Person` serializovat třídu (uvedená v následujícím ukázkovém kódu), <xref:System.Runtime.Serialization.DataContractSerializer> protože to není platná třída kontraktu dat.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Atribut lze použít <xref:System.Runtime.Serialization.DataContractAttribute> pro `Person` třídu, ale to není vždy možné. Například `Person` Třída může být definována v samostatném sestavení, přes které nemáte žádné řízení.  
  
 Vzhledem k tomuto omezení je jednou z možností, jak serializovat `Person` třídu, nahradit ji jinou třídou, která je označena <xref:System.Runtime.Serialization.DataContractAttribute> a zkopírována do nové třídy v nezbytných datech. Cílem je, aby se `Person` Třída zobrazila jako kontrakt DataContract k <xref:System.Runtime.Serialization.DataContractSerializer> . Všimněte si, že toto je jeden ze způsobů, jak serializovat třídy kontraktů, které neobsahují data.  
  
 Ukázka logicky nahrazuje `Person` třídu jinou třídou s názvem `PersonSurrogated` .  
  
```csharp
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
  
 K dosažení této náhrady se používá náhrada za kontrakt dat. Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> . V této ukázce `AllowNonSerializableTypesSurrogate` Třída implementuje toto rozhraní.  
  
 V implementaci rozhraní je prvním úkolem vytvořit mapování typu z `Person` na `PersonSurrogated` . To se používá v době serializace i v době exportu schématu. Toto mapování se dosahuje implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29>Metoda mapuje `Person` instanci na `PersonSurrogated` instanci během serializace, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29>Metoda poskytuje zpětné mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
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
  
 Chcete-li namapovat `PersonSurrogated` kontrakt dat na existující `Person` třídu během importu schématu, ukázka implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> metodu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
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
  
 Následující vzorový kód dokončí implementaci <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
```csharp
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
  
 V této ukázce je náhrada povolena ve ServiceModel podle atributu s názvem `AllowNonSerializableTypesAttribute` . Vývojáři by museli použít tento atribut u kontraktu služby, jak je uvedeno `IPersonnelDataService` výše v kontraktu služby. Tento atribut implementuje `IContractBehavior` a nastaví náhradní operace v rámci svých `ApplyClientBehavior` `ApplyDispatchBehavior` metod a.  
  
 Atribut není v tomto případě nezbytný – používá se pro demonstrační účely v této ukázce. Uživatelé můžou alternativu povolit ručním přidáním podobného `IContractBehavior` `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.  
  
 `IContractBehavior`Implementace vyhledá operace, které používají DataContract, kontrolou, jestli mají `DataContractSerializerOperationBehavior` registrovanou. Pokud k tomu dojde, nastaví `DataContractSurrogate` vlastnost v tomto chování. Následující vzorový kód ukazuje, jak je to hotové. Nastavení náhrady při této operaci umožňuje pro serializaci a deserializaci.  
  
```csharp
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
  
 Před generováním metadat je třeba provést další kroky, aby se zavedlo připojení k použití. Jeden z mechanismů, jak to udělat, je poskytnout, `IWsdlExportExtension` což je to, co ukazuje tento příklad. Další možností je změnit `WsdlExporter` přímo.  
  
 `AllowNonSerializableTypesAttribute`Atribut implementuje `IWsdlExportExtension` a `IContractBehavior` . Přípona může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě. Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje nahradit ho přidáním do `XsdDataContractExporter` používaného během generování schématu pro kontrakt DataContract. Následující fragment kódu ukazuje, jak to provést.  
  
```csharp
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
  
 Při spuštění ukázky klient volá AddEmployee následovaný voláním GetEmployee, aby zkontroloval, zda bylo první volání úspěšné. Výsledek žádosti o operaci GetEmployee se zobrazí v okně konzoly klienta. Operace GetEmployee musí být úspěšná při hledání zaměstnance a tisku "Nalezeno".  
  
> [!NOTE]
> V této ukázce se dozvíte, jak připojit náhradu za serializaci, deserializaci a generování metadat. Neukazuje, jak připojit náhradu pro generování kódu z metadat. Chcete-li zobrazit ukázku, jak lze použít náhradní připojení k vytváření kódu klienta, přečtěte si ukázku [vlastní publikace WSDL](custom-wsdl-publication.md) .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# řešení, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
