---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 436c5778487e6cd272ba3a873be9d243a427db97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953490"
---
# <a name="datacontract-surrogate"></a>Náhrada kontraktu dat
Tato ukázka předvádí, jak lze upravit procesy jako serializace, deserializace, Export schématu a import schématu pomocí náhradní třídy kontraktu dat. V této ukázce se dozvíte, jak použít náhradu ve scénáři klienta a serveru, kde jsou data serializována a přenášena mezi klientem a službou Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
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
  
 Tato `AddEmployee` operace umožňuje uživatelům přidávat data o nových zaměstnancích `GetEmployee` a operace podporuje hledání zaměstnanců na základě názvu.  
  
 Tyto operace používají následující datový typ:  
  
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
  
 V typu není možné <xref:System.Runtime.Serialization.DataContractSerializer> serializovat třídu(uvedenávnásledujícímukázkovémkódu),protožetoneníplatnátřídakontraktudat.`Person` `Employee`  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Atribut lze použít `Person` pro třídu, ale to není vždy možné. Například `Person` třída může být definována v samostatném sestavení, přes které nemáte žádné řízení.  
  
 Vzhledem k tomuto omezení je jednou z možností, `Person` jak serializovat třídu, nahradit ji jinou třídou, která je <xref:System.Runtime.Serialization.DataContractAttribute> označena a zkopírována do nové třídy v nezbytných datech. Cílem je `Person` , aby se třída zobrazila jako kontrakt DataContract <xref:System.Runtime.Serialization.DataContractSerializer>k. Všimněte si, že toto je jeden ze způsobů, jak serializovat třídy kontraktů, které neobsahují data.  
  
 Ukázka logicky nahrazuje `Person` třídu jinou třídou s názvem `PersonSurrogated`.  
  
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
  
 K dosažení této náhrady se používá náhrada za kontrakt dat. Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. V této ukázce `AllowNonSerializableTypesSurrogate` třída implementuje toto rozhraní.  
  
 V implementaci rozhraní je prvním úkolem vytvořit mapování typu z `Person` na. `PersonSurrogated` To se používá v době serializace i v době exportu schématu. Toto mapování se dosahuje implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.  
  
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
  
 Metoda mapuje instanci na`PersonSurrogated` instanci během serializace, jak je znázorněno v následujícím ukázkovém kódu. `Person` <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29>  
  
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
  
 Chcete-li `PersonSurrogated` namapovat kontrakt dat na `Person` existující třídu během importu schématu <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> , ukázka implementuje metodu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Následující vzorový kód dokončí implementaci <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
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
  
 V této ukázce je náhrada povolena ve ServiceModel podle atributu s názvem `AllowNonSerializableTypesAttribute`. Vývojáři by museli použít tento atribut u kontraktu služby, jak je `IPersonnelDataService` uvedeno výše v kontraktu služby. Tento atribut implementuje `IContractBehavior` a nastaví náhradní operace v rámci svých `ApplyClientBehavior` metod a `ApplyDispatchBehavior` .  
  
 Atribut není v tomto případě nezbytný – používá se pro demonstrační účely v této ukázce. Uživatelé můžou alternativu povolit ručním přidáním podobného `IContractBehavior` `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.  
  
 Implementace vyhledá operace, které používají DataContract, kontrolou, jestli `DataContractSerializerOperationBehavior` mají registrovanou. `IContractBehavior` Pokud k tomu dojde, nastaví `DataContractSurrogate` vlastnost v tomto chování. Následující vzorový kód ukazuje, jak je to hotové. Nastavení náhrady při této operaci umožňuje pro serializaci a deserializaci.  
  
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
  
 Před generováním metadat je třeba provést další kroky, aby se zavedlo připojení k použití. Jeden z mechanismů, jak to udělat, `IWsdlExportExtension` je poskytnout, což je to, co ukazuje tento příklad. Další možností je změnit `WsdlExporter` přímo.  
  
 Atribut implementuje `IWsdlExportExtension` a`IContractBehavior`. `AllowNonSerializableTypesAttribute` Přípona může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě. Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje nahradit ho přidáním `XsdDataContractExporter` do používaného během generování schématu pro kontrakt DataContract. Následující fragment kódu ukazuje, jak to provést.  
  
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
  
 Při spuštění ukázky klient volá AddEmployee následovaný voláním GetEmployee, aby zkontroloval, zda bylo první volání úspěšné. Výsledek žádosti o operaci GetEmployee se zobrazí v okně konzoly klienta. Operace GetEmployee musí být úspěšná při hledání zaměstnance a tisku "Nalezeno".  
  
> [!NOTE]
> V této ukázce se dozvíte, jak připojit náhradu za serializaci, deserializaci a generování metadat. Neukazuje, jak připojit náhradu pro generování kódu z metadat. Chcete-li zobrazit ukázku, jak lze použít náhradní připojení k vytváření kódu klienta, přečtěte si ukázku [vlastní publikace WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici řešení, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
