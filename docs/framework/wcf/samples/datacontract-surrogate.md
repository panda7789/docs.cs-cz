---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: f08226d3d871caea2dea3eeaf1cd411557853e45
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976719"
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
  
 Operace `AddEmployee` umožňuje uživatelům přidávat data o nových zaměstnancích a operace `GetEmployee` podporuje hledání zaměstnanců na základě jména.  
  
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
  
 V `Employee` typ nemůže být třída `Person` (uvedená v následujícím ukázkovém kódu) serializována <xref:System.Runtime.Serialization.DataContractSerializer>, protože se nejedná o platnou třídu kontraktu dat.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Atribut <xref:System.Runtime.Serialization.DataContractAttribute> lze použít pro třídu `Person`, ale to není vždy možné. Například třída `Person` může být definována v samostatném sestavení, přes které nemáte žádné řízení.  
  
 Vzhledem k tomuto omezení je jedním ze způsobů, jak serializovat třídu `Person`, nahradit ji jinou třídou, která je označena <xref:System.Runtime.Serialization.DataContractAttribute> a kopírovat data potřebná do nové třídy. Cílem je, aby se třída `Person` jako kontrakt dat <xref:System.Runtime.Serialization.DataContractSerializer>. Všimněte si, že toto je jeden ze způsobů, jak serializovat třídy kontraktů, které neobsahují data.  
  
 Ukázka logicky nahrazuje třídu `Person` jinou třídou s názvem `PersonSurrogated`.  
  
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
  
 K dosažení této náhrady se používá náhrada za kontrakt dat. Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. V této ukázce třída `AllowNonSerializableTypesSurrogate` implementuje toto rozhraní.  
  
 V implementaci rozhraní je prvním úkolem vytvořit mapování typu z `Person` na `PersonSurrogated`. To se používá v době serializace i v době exportu schématu. Toto mapování se dosahuje implementací metody <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29>.  
  
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
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje instanci `Person` na instanci `PersonSurrogated` během serializace, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> poskytuje zpětné mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Chcete-li namapovat kontrakt dat `PersonSurrogated` na existující třídu `Person` během importu schématu, ukázka implementuje metodu <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29>, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Následující vzorový kód dokončí implementaci rozhraní <xref:System.Runtime.Serialization.IDataContractSurrogate>.  
  
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
  
 V této ukázce je náhrada povolena ve ServiceModel podle atributu s názvem `AllowNonSerializableTypesAttribute`. Vývojáři by museli tento atribut uplatnit u kontraktu služby, jak je uvedeno výše v kontraktu služby `IPersonnelDataService`. Tento atribut implementuje `IContractBehavior` a nastaví náhradní operace v rámci svých metod `ApplyClientBehavior` a `ApplyDispatchBehavior`.  
  
 Atribut není v tomto případě nezbytný – používá se pro demonstrační účely v této ukázce. Uživatelé mohou alternativně povolit náhradu ručním přidáním podobného `IContractBehavior`, `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.  
  
 Implementace `IContractBehavior` vyhledá operace, které používají DataContract, kontrolou, jestli mají `DataContractSerializerOperationBehavior` zaregistrované. Pokud k tomu dojde, nastaví vlastnost `DataContractSurrogate` v tomto chování. Následující vzorový kód ukazuje, jak je to hotové. Nastavení náhrady při této operaci umožňuje pro serializaci a deserializaci.  
  
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
  
 Před generováním metadat je třeba provést další kroky, aby se zavedlo připojení k použití. Jedním z mechanismů, jak to provést, je poskytnout `IWsdlExportExtension`, což je to, co ukazuje tento příklad. Dalším způsobem je přímá změna `WsdlExporter`.  
  
 Atribut `AllowNonSerializableTypesAttribute` implementuje `IWsdlExportExtension` a `IContractBehavior`. V tomto případě může být rozšíření buď `IContractBehavior`, nebo `IEndpointBehavior`. Jeho implementace metody `IWsdlExportExtension.ExportContract` umožňuje nahradit ho přidáním do `XsdDataContractExporter` používaného během generování schématu pro kontrakt DataContract. Následující fragment kódu ukazuje, jak to provést.  
  
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
> V této ukázce se dozvíte, jak připojit náhradu za serializaci, deserializaci a generování metadat. Neukazuje, jak připojit náhradu pro generování kódu z metadat. Chcete-li zobrazit ukázku, jak lze použít náhradní připojení k vytváření kódu klienta, přečtěte si ukázku [vlastní publikace WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici řešení, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
