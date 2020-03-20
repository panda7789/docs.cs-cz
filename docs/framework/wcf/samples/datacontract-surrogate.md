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
# <a name="datacontract-surrogate"></a><span data-ttu-id="1408a-102">Náhrada kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="1408a-102">DataContract Surrogate</span></span>
<span data-ttu-id="1408a-103">Tato ukázka ukazuje, jak lze přizpůsobit procesy, jako je serializace, deserializace, export schématu a import schématu pomocí třídy náhradní smlouvy dat.</span><span class="sxs-lookup"><span data-stu-id="1408a-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="1408a-104">Tato ukázka ukazuje, jak použít náhradní v případě klienta a serveru, kde jsou data serializována a přenášena mezi klientem a službou WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="1408a-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1408a-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1408a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1408a-106">Ukázka používá následující servisní smlouvu:</span><span class="sxs-lookup"><span data-stu-id="1408a-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="1408a-107">Operace `AddEmployee` umožňuje uživatelům přidávat data o `GetEmployee` nových zaměstnancích a operace podporuje vyhledávání zaměstnanců na základě názvu.</span><span class="sxs-lookup"><span data-stu-id="1408a-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="1408a-108">Tyto operace používají následující datový typ:</span><span class="sxs-lookup"><span data-stu-id="1408a-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="1408a-109">V `Employee` typu třídy `Person` (uvedené v následujícím ukázkovém kódu) <xref:System.Runtime.Serialization.DataContractSerializer> nelze serializovat, protože není platnou třídou smlouvy dat.</span><span class="sxs-lookup"><span data-stu-id="1408a-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="1408a-110">Atribut můžete <xref:System.Runtime.Serialization.DataContractAttribute> použít na `Person` třídu, ale to není vždy možné.</span><span class="sxs-lookup"><span data-stu-id="1408a-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="1408a-111">Například `Person` třída může být definována v samostatném sestavení, přes které nemáte žádný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1408a-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="1408a-112">Vzhledem k tomuto omezení je `Person` jedním ze způsobů serializace třídy <xref:System.Runtime.Serialization.DataContractAttribute> nahrazení jiné třídy, která je označena a zkopírována přes potřebná data do nové třídy.</span><span class="sxs-lookup"><span data-stu-id="1408a-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="1408a-113">Cílem je, aby `Person` se třída zobrazila jako DataContract na <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1408a-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1408a-114">Všimněte si, že se jedná o jeden způsob serializace tříd y smluv bez dat.</span><span class="sxs-lookup"><span data-stu-id="1408a-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="1408a-115">Ukázka logicky nahradí `Person` třídu jinou `PersonSurrogated`třídou s názvem .</span><span class="sxs-lookup"><span data-stu-id="1408a-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="1408a-116">Náhradní kontrakt dat se používá k dosažení tohoto nahrazení.</span><span class="sxs-lookup"><span data-stu-id="1408a-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="1408a-117">Náhradní kontrakt dat je třída, <xref:System.Runtime.Serialization.IDataContractSurrogate>která implementuje .</span><span class="sxs-lookup"><span data-stu-id="1408a-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="1408a-118">V této ukázce třídy implementuje `AllowNonSerializableTypesSurrogate` toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1408a-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="1408a-119">V implementaci rozhraní je prvním úkolem vytvořit `Person` mapování `PersonSurrogated`typů z na .</span><span class="sxs-lookup"><span data-stu-id="1408a-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="1408a-120">Používá se jak v době serializace, tak v době exportu schématu.</span><span class="sxs-lookup"><span data-stu-id="1408a-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="1408a-121">Toto mapování je dosaženo <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> implementací metody.</span><span class="sxs-lookup"><span data-stu-id="1408a-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="1408a-122">Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje `Person` instanci na `PersonSurrogated` instanci během serializace, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1408a-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1408a-123">Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> poskytuje zpětné mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1408a-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1408a-124">Chcete-li `PersonSurrogated` namapovat `Person` kontrakt dat na existující třídu během <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> importu schématu, ukázka implementuje metodu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1408a-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1408a-125">Následující ukázkový kód dokončí implementaci <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1408a-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="1408a-126">V této ukázce je náhradní povolena `AllowNonSerializableTypesAttribute`v ServiceModel atributem s názvem .</span><span class="sxs-lookup"><span data-stu-id="1408a-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="1408a-127">Vývojáři by museli použít tento atribut na `IPersonnelDataService` své servisní smlouvě, jak je uvedeno ve smlouvě o poskytování služeb výše.</span><span class="sxs-lookup"><span data-stu-id="1408a-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="1408a-128">Tento atribut `IContractBehavior` implementuje a nastavuje `ApplyClientBehavior` `ApplyDispatchBehavior` náhradní na operace v jeho a metody.</span><span class="sxs-lookup"><span data-stu-id="1408a-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="1408a-129">Atribut není v tomto případě nutný - používá se pro demonstrační účely v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="1408a-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="1408a-130">Uživatelé mohou alternativně povolit náhradní `IContractBehavior`ručním přidáním podobného , `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1408a-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="1408a-131">Implementace `IContractBehavior` hledá operace, které používají DataContract kontrolou, `DataContractSerializerOperationBehavior` pokud mají registrované.</span><span class="sxs-lookup"><span data-stu-id="1408a-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="1408a-132">Pokud ano, nastaví `DataContractSurrogate` vlastnost na toto chování.</span><span class="sxs-lookup"><span data-stu-id="1408a-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="1408a-133">Následující ukázkový kód ukazuje, jak se to provádí.</span><span class="sxs-lookup"><span data-stu-id="1408a-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="1408a-134">Nastavení náhradníka pro toto chování operace umožňuje serializaci a rekonstrukci.</span><span class="sxs-lookup"><span data-stu-id="1408a-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="1408a-135">Další kroky je třeba provést k připojení náhradníka pro použití během generování metadat.</span><span class="sxs-lookup"><span data-stu-id="1408a-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="1408a-136">Jedním z mechanismů k tomu `IWsdlExportExtension` je poskytnout, což je to, co tento vzorek demonstruje.</span><span class="sxs-lookup"><span data-stu-id="1408a-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="1408a-137">Dalším způsobem je `WsdlExporter` upravit přímo.</span><span class="sxs-lookup"><span data-stu-id="1408a-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="1408a-138">Atribut `AllowNonSerializableTypesAttribute` `IWsdlExportExtension` implementuje `IContractBehavior`a .</span><span class="sxs-lookup"><span data-stu-id="1408a-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="1408a-139">Rozšíření může být `IContractBehavior` buď `IEndpointBehavior` nebo v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="1408a-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="1408a-140">Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje náhradní přidáním do použité během `XsdDataContractExporter` generování schématu pro DataContract.</span><span class="sxs-lookup"><span data-stu-id="1408a-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="1408a-141">Následující fragment kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="1408a-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="1408a-142">Při spuštění ukázky klient volá AddEmployee následuje GetEmployee volání zkontrolovat, pokud první volání bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1408a-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="1408a-143">Výsledek požadavku operace GetEmployee se zobrazí v okně klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="1408a-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="1408a-144">Operace GetEmployee musí úspěšně najít zaměstnance a vytisknout "nalezeno".</span><span class="sxs-lookup"><span data-stu-id="1408a-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1408a-145">Tato ukázka ukazuje, jak připojit náhradní pro serializovat, rekonstruovat a generování metadat.</span><span class="sxs-lookup"><span data-stu-id="1408a-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="1408a-146">Neukazuje, jak připojit náhradníka pro generování kódu z metadat.</span><span class="sxs-lookup"><span data-stu-id="1408a-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="1408a-147">Chcete-li zobrazit ukázku, jak lze použít náhradní připojit do generování kódu klienta, naleznete [v tématu vlastní WSDL publikace](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) ukázku.</span><span class="sxs-lookup"><span data-stu-id="1408a-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1408a-148">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1408a-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1408a-149">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1408a-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1408a-150">Chcete-li vytvořit edici c# řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1408a-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1408a-151">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1408a-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1408a-152">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="1408a-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1408a-153">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="1408a-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1408a-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1408a-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1408a-155">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1408a-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
