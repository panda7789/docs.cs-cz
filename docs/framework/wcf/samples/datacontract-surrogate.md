---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 7ef78c4361c055d7be35c03a3c8717e86aceddab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183838"
---
# <a name="datacontract-surrogate"></a>Náhrada kontraktu dat
Tato ukázka ukazuje, jak lze přizpůsobit procesy, jako je serializace, deserializace, export schématu a import schématu pomocí třídy náhradní smlouvy dat. Tato ukázka ukazuje, jak použít náhradní v případě klienta a serveru, kde jsou data serializována a přenášena mezi klientem a službou WCF (Windows Communication Foundation).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ukázka používá následující servisní smlouvu:  
  
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
  
 Operace `AddEmployee` umožňuje uživatelům přidávat data o `GetEmployee` nových zaměstnancích a operace podporuje vyhledávání zaměstnanců na základě názvu.  
  
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
  
 V `Employee` typu třídy `Person` (uvedené v následujícím ukázkovém kódu) <xref:System.Runtime.Serialization.DataContractSerializer> nelze serializovat, protože není platnou třídou smlouvy dat.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Atribut můžete <xref:System.Runtime.Serialization.DataContractAttribute> použít na `Person` třídu, ale to není vždy možné. Například `Person` třída může být definována v samostatném sestavení, přes které nemáte žádný ovládací prvek.  
  
 Vzhledem k tomuto omezení je `Person` jedním ze způsobů serializace třídy <xref:System.Runtime.Serialization.DataContractAttribute> nahrazení jiné třídy, která je označena a zkopírována přes potřebná data do nové třídy. Cílem je, aby `Person` se třída zobrazila jako DataContract na <xref:System.Runtime.Serialization.DataContractSerializer>. Všimněte si, že se jedná o jeden způsob serializace tříd y smluv bez dat.  
  
 Ukázka logicky nahradí `Person` třídu jinou `PersonSurrogated`třídou s názvem .  
  
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
  
 Náhradní kontrakt dat se používá k dosažení tohoto nahrazení. Náhradní kontrakt dat je třída, <xref:System.Runtime.Serialization.IDataContractSurrogate>která implementuje . V této ukázce třídy implementuje `AllowNonSerializableTypesSurrogate` toto rozhraní.  
  
 V implementaci rozhraní je prvním úkolem vytvořit `Person` mapování `PersonSurrogated`typů z na . Používá se jak v době serializace, tak v době exportu schématu. Toto mapování je dosaženo <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> implementací metody.  
  
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
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje `Person` instanci na `PersonSurrogated` instanci během serializace, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Chcete-li `PersonSurrogated` namapovat `Person` kontrakt dat na existující třídu během <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> importu schématu, ukázka implementuje metodu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Následující ukázkový kód dokončí implementaci <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
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
  
 V této ukázce je náhradní povolena `AllowNonSerializableTypesAttribute`v ServiceModel atributem s názvem . Vývojáři by museli použít tento atribut na `IPersonnelDataService` své servisní smlouvě, jak je uvedeno ve smlouvě o poskytování služeb výše. Tento atribut `IContractBehavior` implementuje a nastavuje `ApplyClientBehavior` `ApplyDispatchBehavior` náhradní na operace v jeho a metody.  
  
 Atribut není v tomto případě nutný - používá se pro demonstrační účely v této ukázce. Uživatelé mohou alternativně povolit náhradní `IContractBehavior`ručním přidáním podobného , `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.  
  
 Implementace `IContractBehavior` hledá operace, které používají DataContract kontrolou, `DataContractSerializerOperationBehavior` pokud mají registrované. Pokud ano, nastaví `DataContractSurrogate` vlastnost na toto chování. Následující ukázkový kód ukazuje, jak se to provádí. Nastavení náhradníka pro toto chování operace umožňuje serializaci a rekonstrukci.  
  
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
  
 Další kroky je třeba provést k připojení náhradníka pro použití během generování metadat. Jedním z mechanismů k tomu `IWsdlExportExtension` je poskytnout, což je to, co tento vzorek demonstruje. Dalším způsobem je `WsdlExporter` upravit přímo.  
  
 Atribut `AllowNonSerializableTypesAttribute` `IWsdlExportExtension` implementuje `IContractBehavior`a . Rozšíření může být `IContractBehavior` buď `IEndpointBehavior` nebo v tomto případě. Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje náhradní přidáním do použité během `XsdDataContractExporter` generování schématu pro DataContract. Následující fragment kódu ukazuje, jak to provést.  
  
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
  
 Při spuštění ukázky klient volá AddEmployee následuje GetEmployee volání zkontrolovat, pokud první volání bylo úspěšné. Výsledek požadavku operace GetEmployee se zobrazí v okně klientské konzole. Operace GetEmployee musí úspěšně najít zaměstnance a vytisknout "nalezeno".  
  
> [!NOTE]
> Tato ukázka ukazuje, jak připojit náhradní pro serializovat, rekonstruovat a generování metadat. Neukazuje, jak připojit náhradníka pro generování kódu z metadat. Chcete-li zobrazit ukázku, jak lze použít náhradní připojit do generování kódu klienta, naleznete [v tématu vlastní WSDL publikace](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) ukázku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit edici c# řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
