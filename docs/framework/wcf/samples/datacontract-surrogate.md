---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 5729943f455d4669f047eb2d86fb7292824c0f2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645415"
---
# <a name="datacontract-surrogate"></a>Náhrada kontraktu dat
Tato ukázka předvádí, jak procesy, jako jsou serializace, deserializace, schéma export a import schématu je možné přizpůsobit pomocí kontraktu dat náhradní třídy. Tento příklad ukazuje způsob použití náhradní ve scénáři klient a server se data serializována a přenosu mezi klienta Windows Communication Foundation (WCF) a služby.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Ukázka používá následující kontraktu služby:  
  
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
  
 `AddEmployee` Operace umožňuje uživatelům přidávat data o nových zaměstnanců a `GetEmployee` operace podporuje vyhledávání pro zaměstnance na základě názvu.  
  
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
  
 V `Employee` typ, `Person` třídy (viz následující ukázka kódu) nelze bylo serializováno modulem <xref:System.Runtime.Serialization.DataContractSerializer> vzhledem k tomu, že se nejedná o platný datový kontrakt třídu.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Můžete použít `DataContract` atribut `Person` třídy, ale to není vždy možné. Například `Person` třídy lze definovat v samostatném sestavení nad tím, které nemají žádnou kontrolu.  
  
 Toto omezení, jeden ze způsobů, jak serializovat daný `Person` třída má nahradit jinou třídu, která je označena `DataContractAttribute` a kopii přes data potřebná pro novou třídu. Cílem je, aby `Person` třídy se zobrazí jako kontraktu DataContract pro <xref:System.Runtime.Serialization.DataContractSerializer>. Všimněte si, že se jedná o jeden způsob, jak třídy bez data smlouvy serializace.  
  
 Ukázka logicky nahradí `Person` třídy s jinou třídu s názvem `PersonSurrogated`.  
  
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
  
 Náhrada kontraktu dat se využívají k dosažení této nahrazení. Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. V této ukázce `AllowNonSerializableTypesSurrogate` třída implementuje toto rozhraní.  
  
 V implementaci rozhraní je první úkol vytvořit mapování typu z `Person` k `PersonSurrogated`. Používá se během serializace i v době exportu schématu. Toto mapování je dosaženo implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Map – metoda `Person` instance na `PersonSurrogated` instancí během serializace, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda poskytuje reverzní mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Mapovat `PersonSurrogated` data smlouvy do existující `Person` třídy při importu schématu, implementuje vzorek <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> způsob, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Následující ukázka kódu dokončí provádění <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
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
  
 V této ukázce je zástupný v ServiceModel stará atribut s názvem `AllowNonSerializableTypesAttribute`. Vývojáři by bylo potřeba použít tento atribut na jejich kontraktu služby, jak je vidět na `IPersonnelDataService` smlouvy o poskytování služeb nahoře. Tento atribut implementuje `IContractBehavior` a nastaví náhradní na operace v jeho `ApplyClientBehavior` a `ApplyDispatchBehavior` metody.  
  
 Atribut není nutné v tomto případě – používá se pro demonstrační účely v této ukázce. Uživatele můžete také povolit náhradní ručním přidáním podobná `IContractBehavior`, `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo konfigurace.  
  
 `IContractBehavior` Vypadá implementaci pro operace, které používají kontraktu dat DataContract kontrolou, jestli mají `DataContractSerializerOperationBehavior` zaregistrovaný. V takovém případě se nastaví `DataContractSurrogate` vlastnosti tohoto chování. Následující ukázkový kód ukazuje, jak to lze provést. Nastavení náhradní na toto chování operace umožňuje k serializaci a deserializaci.  
  
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
  
 Další kroky je třeba provést k nahrazení pro použití při generování metadat. Jeden mechanismus k tomu je poskytnout `IWsdlExportExtension` což je, co v této ukázce. Dalším způsobem, je změnit `WsdlExporter` přímo.  
  
 `AllowNonSerializableTypesAttribute` Atribut implementuje `IWsdlExportExtension` a `IContractBehavior`. Rozšíření může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě. Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje zástupný tak, že přidáte tak, `XsdDataContractExporter` používá při generování schématu pro kontraktu dat DataContract. Následující fragment kódu ukazuje, jak to provést.  
  
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
  
 Když spustíte ukázku, klient volá AddEmployee následovanou voláním GetEmployee ke kontrole, pokud první volání bylo úspěšné. Výsledek operace požadavku GetEmployee se zobrazí v okně konzoly klienta. Operace GetEmployee musí být úspěšné při hledání zaměstnance a vytisknout "nenalezeno".  
  
> [!NOTE]
>  Tato ukázka předvádí, jak zařadit náhradní pro serializace, deserializaci a generování metadat. Tom, jak zařadit náhradní pro generování kódu z metadat není uveden. Chcete-li zobrazit ukázku, jak náhradní umožňuje pružný generování kódu klienta, přečtěte si téma [vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) vzorku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice C# řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Viz také:
