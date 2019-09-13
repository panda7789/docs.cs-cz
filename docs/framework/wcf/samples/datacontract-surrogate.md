---
title: Náhrada kontraktu dat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 32ac0b82a637e2fb1a62b81555648942d31c30de
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928607"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="c4633-102">Náhrada kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="c4633-102">DataContract Surrogate</span></span>
<span data-ttu-id="c4633-103">Tato ukázka předvádí, jak lze upravit procesy jako serializace, deserializace, Export schématu a import schématu pomocí náhradní třídy kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="c4633-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="c4633-104">V této ukázce se dozvíte, jak použít náhradu ve scénáři klienta a serveru, kde jsou data serializována a přenášena mezi klientem a službou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c4633-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4633-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c4633-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c4633-106">Ukázka používá následující kontrakt služby:</span><span class="sxs-lookup"><span data-stu-id="c4633-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="c4633-107">Tato `AddEmployee` operace umožňuje uživatelům přidávat data o nových zaměstnancích `GetEmployee` a operace podporuje hledání zaměstnanců na základě názvu.</span><span class="sxs-lookup"><span data-stu-id="c4633-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="c4633-108">Tyto operace používají následující datový typ:</span><span class="sxs-lookup"><span data-stu-id="c4633-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="c4633-109">V typu není možné <xref:System.Runtime.Serialization.DataContractSerializer> serializovat třídu(uvedenávnásledujícímukázkovémkódu),protožetoneníplatnátřídakontraktudat.`Person` `Employee`</span><span class="sxs-lookup"><span data-stu-id="c4633-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="c4633-110"><xref:System.Runtime.Serialization.DataContractAttribute> Atribut lze použít `Person` pro třídu, ale to není vždy možné.</span><span class="sxs-lookup"><span data-stu-id="c4633-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="c4633-111">Například `Person` třída může být definována v samostatném sestavení, přes které nemáte žádné řízení.</span><span class="sxs-lookup"><span data-stu-id="c4633-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="c4633-112">Vzhledem k tomuto omezení je jednou z možností, `Person` jak serializovat třídu, nahradit ji jinou třídou, která je <xref:System.Runtime.Serialization.DataContractAttribute> označena a zkopírována do nové třídy v nezbytných datech.</span><span class="sxs-lookup"><span data-stu-id="c4633-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="c4633-113">Cílem je `Person` , aby se třída zobrazila jako kontrakt DataContract <xref:System.Runtime.Serialization.DataContractSerializer>k.</span><span class="sxs-lookup"><span data-stu-id="c4633-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c4633-114">Všimněte si, že toto je jeden ze způsobů, jak serializovat třídy kontraktů, které neobsahují data.</span><span class="sxs-lookup"><span data-stu-id="c4633-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="c4633-115">Ukázka logicky nahrazuje `Person` třídu jinou třídou s názvem `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="c4633-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="c4633-116">K dosažení této náhrady se používá náhrada za kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="c4633-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="c4633-117">Náhrada kontraktu dat je třída, která implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span><span class="sxs-lookup"><span data-stu-id="c4633-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="c4633-118">V této ukázce `AllowNonSerializableTypesSurrogate` třída implementuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4633-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="c4633-119">V implementaci rozhraní je prvním úkolem vytvořit mapování typu z `Person` na. `PersonSurrogated`</span><span class="sxs-lookup"><span data-stu-id="c4633-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="c4633-120">To se používá v době serializace i v době exportu schématu.</span><span class="sxs-lookup"><span data-stu-id="c4633-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="c4633-121">Toto mapování se dosahuje implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.</span><span class="sxs-lookup"><span data-stu-id="c4633-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="c4633-122">Metoda mapuje instanci na`PersonSurrogated` instanci během serializace, jak je znázorněno v následujícím ukázkovém kódu. `Person` <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29></span><span class="sxs-lookup"><span data-stu-id="c4633-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c4633-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda poskytuje zpětné mapování pro deserializaci, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c4633-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c4633-124">Chcete-li `PersonSurrogated` namapovat kontrakt dat na `Person` existující třídu během importu schématu <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> , ukázka implementuje metodu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c4633-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c4633-125">Následující vzorový kód dokončí implementaci <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4633-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="c4633-126">V této ukázce je náhrada povolena ve ServiceModel podle atributu s názvem `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="c4633-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="c4633-127">Vývojáři by museli použít tento atribut u kontraktu služby, jak je `IPersonnelDataService` uvedeno výše v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="c4633-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="c4633-128">Tento atribut implementuje `IContractBehavior` a nastaví náhradní operace v rámci svých `ApplyClientBehavior` metod a `ApplyDispatchBehavior` .</span><span class="sxs-lookup"><span data-stu-id="c4633-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="c4633-129">Atribut není v tomto případě nezbytný – používá se pro demonstrační účely v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c4633-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="c4633-130">Uživatelé můžou alternativu povolit ručním přidáním podobného `IContractBehavior` `IEndpointBehavior` nebo `IOperationBehavior` pomocí kódu nebo pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c4633-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="c4633-131">Implementace vyhledá operace, které používají DataContract, kontrolou, jestli `DataContractSerializerOperationBehavior` mají registrovanou. `IContractBehavior`</span><span class="sxs-lookup"><span data-stu-id="c4633-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="c4633-132">Pokud k tomu dojde, nastaví `DataContractSurrogate` vlastnost v tomto chování.</span><span class="sxs-lookup"><span data-stu-id="c4633-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="c4633-133">Následující vzorový kód ukazuje, jak je to hotové.</span><span class="sxs-lookup"><span data-stu-id="c4633-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="c4633-134">Nastavení náhrady při této operaci umožňuje pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c4633-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="c4633-135">Před generováním metadat je třeba provést další kroky, aby se zavedlo připojení k použití.</span><span class="sxs-lookup"><span data-stu-id="c4633-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="c4633-136">Jeden z mechanismů, jak to udělat, `IWsdlExportExtension` je poskytnout, což je to, co ukazuje tento příklad.</span><span class="sxs-lookup"><span data-stu-id="c4633-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="c4633-137">Další možností je změnit `WsdlExporter` přímo.</span><span class="sxs-lookup"><span data-stu-id="c4633-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="c4633-138">Atribut implementuje `IWsdlExportExtension` a`IContractBehavior`. `AllowNonSerializableTypesAttribute`</span><span class="sxs-lookup"><span data-stu-id="c4633-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="c4633-139">Přípona může být buď `IContractBehavior` nebo `IEndpointBehavior` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="c4633-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="c4633-140">Jeho `IWsdlExportExtension.ExportContract` implementace metody umožňuje nahradit ho přidáním `XsdDataContractExporter` do používaného během generování schématu pro kontrakt DataContract.</span><span class="sxs-lookup"><span data-stu-id="c4633-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="c4633-141">Následující fragment kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="c4633-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="c4633-142">Při spuštění ukázky klient volá AddEmployee následovaný voláním GetEmployee, aby zkontroloval, zda bylo první volání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="c4633-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="c4633-143">Výsledek žádosti o operaci GetEmployee se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="c4633-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="c4633-144">Operace GetEmployee musí být úspěšná při hledání zaměstnance a tisku "Nalezeno".</span><span class="sxs-lookup"><span data-stu-id="c4633-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4633-145">V této ukázce se dozvíte, jak připojit náhradu za serializaci, deserializaci a generování metadat.</span><span class="sxs-lookup"><span data-stu-id="c4633-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="c4633-146">Neukazuje, jak připojit náhradu pro generování kódu z metadat.</span><span class="sxs-lookup"><span data-stu-id="c4633-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="c4633-147">Chcete-li zobrazit ukázku, jak lze použít náhradní připojení k vytváření kódu klienta, přečtěte si ukázku [vlastní publikace WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) .</span><span class="sxs-lookup"><span data-stu-id="c4633-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4633-148">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c4633-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c4633-149">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4633-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c4633-150">Pokud chcete vytvořit C# edici řešení, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4633-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c4633-151">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4633-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c4633-152">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="c4633-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4633-153">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c4633-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c4633-154">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="c4633-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4633-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c4633-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
