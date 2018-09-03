---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 10b0c2a3e82e39b03291f567ca360c51042b464e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466594"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="9c451-102">Náhrada kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="9c451-102">DataContract Surrogate</span></span>
<span data-ttu-id="9c451-103">Tato ukázka předvádí, jak procesy, jako jsou serializace, deserializace, schéma export a import schématu je možné přizpůsobit pomocí kontraktu dat náhradní třídy.</span><span class="sxs-lookup"><span data-stu-id="9c451-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="9c451-104">Tento příklad ukazuje způsob použití náhradní ve scénáři klient a server se data serializována a přenosu mezi klienta Windows Communication Foundation (WCF) a služby.</span><span class="sxs-lookup"><span data-stu-id="9c451-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c451-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9c451-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9c451-106">Ukázka používá následující kontraktu služby:</span><span class="sxs-lookup"><span data-stu-id="9c451-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="9c451-107">`AddEmployee` Operace umožňuje uživatelům přidávat data o nových zaměstnanců a `GetEmployee` operace podporuje vyhledávání pro zaměstnance na základě názvu.</span><span class="sxs-lookup"><span data-stu-id="9c451-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="9c451-108">Tyto operace použijte následující datový typ:</span><span class="sxs-lookup"><span data-stu-id="9c451-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="9c451-109">V `Employee` typ, `Person` třídy (viz následující ukázka kódu) nelze bylo serializováno modulem <xref:System.Runtime.Serialization.DataContractSerializer> vzhledem k tomu, že se nejedná o platný datový kontrakt třídu.</span><span class="sxs-lookup"><span data-stu-id="9c451-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="9c451-110">Můžete použít `DataContract` atribut `Person` třídy, ale to není vždy možné.</span><span class="sxs-lookup"><span data-stu-id="9c451-110">You can apply the `DataContract` attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="9c451-111">Například `Person` třídy lze definovat v samostatném sestavení nad tím, které nemají žádnou kontrolu.</span><span class="sxs-lookup"><span data-stu-id="9c451-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="9c451-112">Toto omezení, jeden ze způsobů, jak serializovat daný `Person` třída má nahradit jinou třídu, která je označena `DataContractAttribute` a kopii přes data potřebná pro novou třídu.</span><span class="sxs-lookup"><span data-stu-id="9c451-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with `DataContractAttribute` and copy over necessary data to the new class.</span></span> <span data-ttu-id="9c451-113">Cílem je, aby `Person` třídy se zobrazí jako kontraktu DataContract pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c451-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="9c451-114">Všimněte si, že se jedná o jeden způsob, jak třídy bez data smlouvy serializace.</span><span class="sxs-lookup"><span data-stu-id="9c451-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="9c451-115">Ukázka logicky nahradí `Person` třídy s jinou třídu s názvem `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="9c451-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="9c451-116">Náhrada kontraktu dat se využívají k dosažení této nahrazení.</span><span class="sxs-lookup"><span data-stu-id="9c451-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="9c451-117">Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="9c451-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="9c451-118">V této ukázce `AllowNonSerializableTypesSurrogate` třída implementuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9c451-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="9c451-119">V implementaci rozhraní je první úkol vytvořit mapování typu z `Person` k `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="9c451-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="9c451-120">Používá se během serializace i v době exportu schématu.</span><span class="sxs-lookup"><span data-stu-id="9c451-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="9c451-121">Toto mapování je dosaženo implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.</span><span class="sxs-lookup"><span data-stu-id="9c451-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="9c451-122"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Map – metoda `Person` instance na `PersonSurrogated` instancí během serializace, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9c451-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="9c451-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda poskytuje reverzní mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9c451-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="9c451-124">Mapovat `PersonSurrogated` data smlouvy do existující `Person` třídy při importu schématu, implementuje vzorek <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> způsob, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9c451-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="9c451-125">Následující ukázka kódu dokončí provádění <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9c451-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="9c451-126">V této ukázce je zástupný v ServiceModel stará atribut s názvem `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="9c451-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="9c451-127">Vývojáři by bylo potřeba použít tento atribut na jejich kontraktu služby, jak je vidět na `IPersonnelDataService` smlouvy o poskytování služeb nahoře.</span><span class="sxs-lookup"><span data-stu-id="9c451-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="9c451-128">Tento atribut implementuje `IContractBehavior` a nastaví náhradní na operace v jeho `ApplyClientBehavior` a `ApplyDispatchBehavior` metody.</span><span class="sxs-lookup"><span data-stu-id="9c451-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="9c451-129">Atribut není nutné v tomto případě – používá se pro demonstrační účely v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="9c451-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="9c451-130">Uživatele můžete také povolit náhradní ručním přidáním podobná `IContractBehavior`, `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9c451-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="9c451-131">`IContractBehavior` Vypadá implementaci pro operace, které používají kontraktu dat DataContract kontrolou, jestli mají `DataContractSerializerOperationBehavior` zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="9c451-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="9c451-132">V takovém případě se nastaví `DataContractSurrogate` vlastnosti tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="9c451-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="9c451-133">Následující ukázkový kód ukazuje, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="9c451-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="9c451-134">Nastavení náhradní na toto chování operace umožňuje k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="9c451-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="9c451-135">Další kroky je třeba provést k nahrazení pro použití při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="9c451-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="9c451-136">Jeden mechanismus k tomu je poskytnout `IWsdlExportExtension` což je, co v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="9c451-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="9c451-137">Dalším způsobem, je změnit `WsdlExporter` přímo.</span><span class="sxs-lookup"><span data-stu-id="9c451-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="9c451-138">`AllowNonSerializableTypesAttribute` Atribut implementuje `IWsdlExportExtension` a `IContractBehavior`.</span><span class="sxs-lookup"><span data-stu-id="9c451-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="9c451-139">Rozšíření může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="9c451-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="9c451-140">Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje zástupný tak, že přidáte tak, `XsdDataContractExporter` používá při generování schématu pro kontraktu dat DataContract.</span><span class="sxs-lookup"><span data-stu-id="9c451-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="9c451-141">Následující fragment kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="9c451-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="9c451-142">Když spustíte ukázku, klient volá AddEmployee následovanou voláním GetEmployee ke kontrole, pokud první volání bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9c451-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="9c451-143">Výsledek operace požadavku GetEmployee se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="9c451-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="9c451-144">Operace GetEmployee musí být úspěšné při hledání zaměstnance a vytisknout "nenalezeno".</span><span class="sxs-lookup"><span data-stu-id="9c451-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c451-145">Tato ukázka předvádí, jak zařadit náhradní pro serializace, deserializaci a generování metadat.</span><span class="sxs-lookup"><span data-stu-id="9c451-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="9c451-146">Tom, jak zařadit náhradní pro generování kódu z metadat není uveden.</span><span class="sxs-lookup"><span data-stu-id="9c451-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="9c451-147">Chcete-li zobrazit ukázku, jak náhradní umožňuje pružný generování kódu klienta, přečtěte si téma [vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="9c451-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c451-148">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9c451-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9c451-149">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c451-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9c451-150">K sestavení edice C# řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c451-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9c451-151">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c451-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c451-152">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9c451-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c451-153">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9c451-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c451-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9c451-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c451-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9c451-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a><span data-ttu-id="9c451-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c451-156">See Also</span></span>
