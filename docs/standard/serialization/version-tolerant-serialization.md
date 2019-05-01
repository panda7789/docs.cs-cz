---
title: Serializace tolerantní vůči verzím verze
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: c899cfe1015a25adc25fc28ee84d0a37a397defe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028249"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="167a4-102">Serializace tolerantní vůči verzím verze</span><span class="sxs-lookup"><span data-stu-id="167a4-102">Version tolerant serialization</span></span>
<span data-ttu-id="167a4-103">Ve verzi 1.0 a 1.1 rozhraní .NET Framework byla problematický vytváření Serializovatelné typy, které by se znovu použít z jedné verze aplikace na další.</span><span class="sxs-lookup"><span data-stu-id="167a4-103">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="167a4-104">V případě typu byl změněn přidáním pole navíc, by se objeví následující problémy:</span><span class="sxs-lookup"><span data-stu-id="167a4-104">If a type was modified by adding extra fields, the following problems would occur:</span></span>  
  
- <span data-ttu-id="167a4-105">Starší verze aplikace by vyvolat výjimky dotaz k deserializaci nové verze původní typu.</span><span class="sxs-lookup"><span data-stu-id="167a4-105">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>  
  
- <span data-ttu-id="167a4-106">Novější verze aplikace by výjimku výjimky, při deserializaci starší verze typu s chybějící data.</span><span class="sxs-lookup"><span data-stu-id="167a4-106">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>  
  
 <span data-ttu-id="167a4-107">Verze chybám serializace (VTS) je sada funkcí zavedena v rozhraní .NET Framework 2.0, který umožňuje snadněji v čase, chcete-li upravit Serializovatelné typy.</span><span class="sxs-lookup"><span data-stu-id="167a4-107">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="167a4-108">Konkrétně jsou povoleny funkce VTS pro třídy, do kterého <xref:System.SerializableAttribute> byl použit atribut, včetně obecných typů.</span><span class="sxs-lookup"><span data-stu-id="167a4-108">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="167a4-109">VTS umožňuje přidat nové pole do těchto tříd bez porušení kompatibilitu s jinými verzemi typu.</span><span class="sxs-lookup"><span data-stu-id="167a4-109">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="167a4-110">Ukázkové aplikace práci, naleznete v tématu [ukázka technologie serializace odolný vůči chybám verze](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="167a4-110">For a working sample application, see [Version Tolerant Serialization Technology Sample](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span></span>  
  
 <span data-ttu-id="167a4-111">Jsou povoleny funkce VTS, používáte-li <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="167a4-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="167a4-112">Navíc povoleny všechny funkce s výjimkou tolerance nadbytečná data také při použití <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="167a4-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="167a4-113">Další informace o použití těchto tříd pro serializaci naleznete v tématu [binární serializace](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="167a4-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="167a4-114">Seznam funkcí</span><span class="sxs-lookup"><span data-stu-id="167a4-114">Feature list</span></span>  
 <span data-ttu-id="167a4-115">Sada funkcí obsahuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="167a4-115">The set of features includes the following:</span></span>  
  
- <span data-ttu-id="167a4-116">Odchylka nadbytečná nebo neočekávaná data.</span><span class="sxs-lookup"><span data-stu-id="167a4-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="167a4-117">To umožňuje novější verze tohoto typu k odesílání dat ke starším verzím.</span><span class="sxs-lookup"><span data-stu-id="167a4-117">This enables newer versions of the type to send data to older versions.</span></span>  
  
- <span data-ttu-id="167a4-118">Odchylka chybějících volitelnými daty.</span><span class="sxs-lookup"><span data-stu-id="167a4-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="167a4-119">To umožňuje starší verze k odesílání dat do novější verze.</span><span class="sxs-lookup"><span data-stu-id="167a4-119">This enables older versions to send data to newer versions.</span></span>  
  
- <span data-ttu-id="167a4-120">Zpětná volání serializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-120">Serialization callbacks.</span></span> <span data-ttu-id="167a4-121">To umožňuje inteligentní výchozí nastavení hodnoty v případech, kdy je chybějící data.</span><span class="sxs-lookup"><span data-stu-id="167a4-121">This enables intelligent default value setting in cases where data is missing.</span></span>  
  
 <span data-ttu-id="167a4-122">Kromě toho je funkce k prohlášení, pokud byl přidán nový volitelné pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="167a4-123">Toto je <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> vlastnost <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="167a4-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>  
  
 <span data-ttu-id="167a4-124">Tyto funkce jsou popsány podrobněji níže.</span><span class="sxs-lookup"><span data-stu-id="167a4-124">These features are discussed in greater detail below.</span></span>  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="167a4-125">Tolerance nadbytečná nebo neočekávaná data</span><span class="sxs-lookup"><span data-stu-id="167a4-125">Tolerance of extraneous or unexpected data</span></span>  
 <span data-ttu-id="167a4-126">Všechna nadbytečná nebo neočekávaná data v minulosti během deserializace způsobeno výjimky, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="167a4-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="167a4-127">S VTS ve stejné situaci, všechna nadbytečná nebo neočekávaná data, je ignorován namísto způsobující výjimky, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="167a4-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="167a4-128">To umožňuje aplikacím, které používají novější verze tohoto typu (to znamená, že verzi, která obsahuje více polí) k odeslání informací do aplikace, které očekávají starších verzích stejného typu.</span><span class="sxs-lookup"><span data-stu-id="167a4-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>  
  
 <span data-ttu-id="167a4-129">V následujícím příkladu doplňující data obsažená v `CountryField` verze 2.0 `Address` třída je ignorována, pokud starší aplikace deserializuje novější verzi.</span><span class="sxs-lookup"><span data-stu-id="167a4-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>  
  
```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  
  
## <a name="tolerance-of-missing-data"></a><span data-ttu-id="167a4-130">Tolerance chybějících dat</span><span class="sxs-lookup"><span data-stu-id="167a4-130">Tolerance of missing data</span></span>  
 <span data-ttu-id="167a4-131">Pole může být označen jako volitelné použitím <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na ně.</span><span class="sxs-lookup"><span data-stu-id="167a4-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="167a4-132">Během deserializace nepovinné údaje chybí, je-li pro Serializační stroj ignoruje absenci a nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="167a4-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="167a4-133">Aplikace, které očekávají starší verze typu tedy můžete odeslat data aplikací, které očekáváte novější verze stejného typu.</span><span class="sxs-lookup"><span data-stu-id="167a4-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>  
  
 <span data-ttu-id="167a4-134">Následující příklad ukazuje, verze 2.0 `Address` třídy s `CountryField` pole označeno jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="167a4-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="167a4-135">Je-li starší aplikace odešle verze 1 a novější aplikace, která očekává verze 2.0, je ignorován neexistují data.</span><span class="sxs-lookup"><span data-stu-id="167a4-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
  
    [OptionalField]  
    public string CountryField;  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
  
    <OptionalField> _  
    Public CountryField As String  
End Class  
```  
  
## <a name="serialization-callbacks"></a><span data-ttu-id="167a4-136">Zpětná volání serializace</span><span class="sxs-lookup"><span data-stu-id="167a4-136">Serialization callbacks</span></span>  
 <span data-ttu-id="167a4-137">Zpětná volání serializace jsou mechanismus, který poskytuje zachytávání do procesu serializaci nebo deserializaci na čtyři body.</span><span class="sxs-lookup"><span data-stu-id="167a4-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>  
  
|<span data-ttu-id="167a4-138">Atribut</span><span class="sxs-lookup"><span data-stu-id="167a4-138">Attribute</span></span>|<span data-ttu-id="167a4-139">Když je volána metoda přidružené</span><span class="sxs-lookup"><span data-stu-id="167a4-139">When the Associated Method is Called</span></span>|<span data-ttu-id="167a4-140">Typické použití</span><span class="sxs-lookup"><span data-stu-id="167a4-140">Typical Use</span></span>|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="167a4-141">Před deserialization.\*</span><span class="sxs-lookup"><span data-stu-id="167a4-141">Before deserialization.\*</span></span>|<span data-ttu-id="167a4-142">Inicializuje výchozí hodnoty pro volitelná pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-142">Initialize default values for optional fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="167a4-143">Po deserializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-143">After deserialization.</span></span>|<span data-ttu-id="167a4-144">Opravte hodnoty volitelné pole založené na obsahu další pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-144">Fix optional field values based on contents of other fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="167a4-145">Před serializací.</span><span class="sxs-lookup"><span data-stu-id="167a4-145">Before serialization.</span></span>|<span data-ttu-id="167a4-146">Připravte pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="167a4-146">Prepare for serialization.</span></span> <span data-ttu-id="167a4-147">Můžete například vytvořte struktury volitelnými daty.</span><span class="sxs-lookup"><span data-stu-id="167a4-147">For example, create optional data structures.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="167a4-148">Po serializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-148">After serialization.</span></span>|<span data-ttu-id="167a4-149">Protokolovat události serializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-149">Log serialization events.</span></span>|  
  
 <span data-ttu-id="167a4-150">\* Toto zpětné volání je volána před konstruktor deserializace, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="167a4-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>  
  
### <a name="using-callbacks"></a><span data-ttu-id="167a4-151">Pomocí zpětných volání</span><span class="sxs-lookup"><span data-stu-id="167a4-151">Using callbacks</span></span>  
 <span data-ttu-id="167a4-152">Chcete-li použít zpětná volání, vztahují na metodu, která přijme příslušný atribut <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="167a4-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="167a4-153">Pouze jednu metodu na třídu může být označena každý z těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="167a4-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="167a4-154">Příklad:</span><span class="sxs-lookup"><span data-stu-id="167a4-154">For example:</span></span>  
  
```csharp  
[OnDeserializing]  
private void SetCountryRegionDefault(StreamingContext sc)  
{  
    CountryField = "Japan";  
}  
```  
  
```vb  
<OnDeserializing>  
Private Sub SetCountryRegionDefault(StreamingContext sc)  
    CountryField = "Japan";  
End Sub  
```  
  
 <span data-ttu-id="167a4-155">Tyto metody slouží pro správu verzí.</span><span class="sxs-lookup"><span data-stu-id="167a4-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="167a4-156">Během deserializace volitelné pole nemusí být správně inicializován Pokud chybí data pro pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="167a4-157">Tento problém lze vyřešit tak, že vytvoření metody, která přiřadí správnou hodnotu, pak buď použití **OnDeserializingAttribute** nebo **OnDeserializedAttribute** atribut do metody.</span><span class="sxs-lookup"><span data-stu-id="167a4-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>  
  
 <span data-ttu-id="167a4-158">Následující příklad ukazuje metodu v souvislosti s typem.</span><span class="sxs-lookup"><span data-stu-id="167a4-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="167a4-159">Je-li starší verzi aplikace odešle instanci `Address` třídy na novější verzi aplikace, `CountryField` pole data budou chybějící.</span><span class="sxs-lookup"><span data-stu-id="167a4-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="167a4-160">Ale po deserializace, bude pole nastavena na výchozí hodnotu "Japonsko."</span><span class="sxs-lookup"><span data-stu-id="167a4-160">But after deserialization, the field will be set to a default value "Japan."</span></span>  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    [OptionalField]  
    public string CountryField;  
  
    [OnDeserializing]  
    private void SetCountryRegionDefault (StreamingContext sc)  
    {  
        CountryField = "Japan";  
    }  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    <OptionalField> _  
    Public CountryField As String  
  
    <OnDeserializing> _  
    Private Sub SetCountryRegionDefault(StreamingContext sc)  
        CountryField = "Japan";  
    End Sub  
End Class  
```  
  
## <a name="the-versionadded-property"></a><span data-ttu-id="167a4-161">Vlastnost VersionAdded</span><span class="sxs-lookup"><span data-stu-id="167a4-161">The VersionAdded property</span></span>  
 <span data-ttu-id="167a4-162">**OptionalFieldAttribute** má **VersionAdded** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="167a4-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="167a4-163">Ve verzi 2.0 rozhraní .NET Framework nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="167a4-163">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="167a4-164">Je však důležité pro nastavení této vlastnosti správně zajistit, že typ bude kompatibilní s moduly budoucí serializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-164">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>  
  
 <span data-ttu-id="167a4-165">Vlastnost určuje, kterou verzi typu bylo přidáno daného pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-165">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="167a4-166">By měla být zvýšena podle právě jeden (počínaje 2) pokaždé, když je změněn na typ, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="167a4-166">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>  
  
```csharp  
// Version 1.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
}  
  
// Version 2.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded = 2)]  
    public string NickName;  
    [OptionalField(VersionAdded = 2)]  
    public DateTime BirthDate;  
}  
  
// Version 3.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded=2)]  
    public string NickName;  
    [OptionalField(VersionAdded=2)]  
    public DateTime BirthDate;  
  
    [OptionalField(VersionAdded=3)]  
    public int Weight;  
}  
```  
  
```vb  
' Version 1.0  
<Serializable> _  
Public Class Person  
    Public FullName  
End Class  
  
' Version 2.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
End Class  
  
' Version 3.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
  
    <OptionalField(VersionAdded := 3)> _  
    Public Weight As Integer  
End Class  
```  
  
## <a name="serializationbinder"></a><span data-ttu-id="167a4-167">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="167a4-167">SerializationBinder</span></span>  
 <span data-ttu-id="167a4-168">Někteří uživatelé muset které třídu k serializaci a deserializaci vzhledem k tomu, že u serverových a klientských je nutné zadat jinou verzi třídy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="167a4-168">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="167a4-169"><xref:System.Runtime.Serialization.SerializationBinder> je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="167a4-169"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span>  <span data-ttu-id="167a4-170">Chcete-li použít tuto třídu, dosáhnout odvozením třídy od <xref:System.Runtime.Serialization.SerializationBinder> a přepište <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="167a4-170">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="167a4-171">Další informace najdete v tématu [řízení serializace a deserializace pomocí SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="167a4-171">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="167a4-172">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="167a4-172">Best practices</span></span>  
 <span data-ttu-id="167a4-173">Chcete-li zajistit správnou verzí chování, postupujte podle těchto pravidel ke změně typu na verzi:</span><span class="sxs-lookup"><span data-stu-id="167a4-173">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>  
  
- <span data-ttu-id="167a4-174">Serializovaná pole nikdy odebrat.</span><span class="sxs-lookup"><span data-stu-id="167a4-174">Never remove a serialized field.</span></span>  
  
- <span data-ttu-id="167a4-175">Nikdy použít <xref:System.NonSerializedAttribute> atributu na pole, pokud atribut nebyl použit na pole v předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="167a4-175">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>  
  
- <span data-ttu-id="167a4-176">Nikdy změnit název nebo typ serializovaného pole.</span><span class="sxs-lookup"><span data-stu-id="167a4-176">Never change the name or the type of a serialized field.</span></span>  
  
- <span data-ttu-id="167a4-177">Při přidávání nového serializovaná pole, použije **OptionalFieldAttribute** atribut.</span><span class="sxs-lookup"><span data-stu-id="167a4-177">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>  
  
- <span data-ttu-id="167a4-178">Při odebírání **NonSerializedAttribute** atribut z pole (tj. nebyla serializovatelný v předchozí verzi), použije **OptionalFieldAttribute** atribut.</span><span class="sxs-lookup"><span data-stu-id="167a4-178">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>  
  
- <span data-ttu-id="167a4-179">U všech polí volitelné, nastavte smysluplné výchozí pomocí zpětných volání serializace, není-li 0 nebo **null** jako výchozí hodnoty jsou přijatelné.</span><span class="sxs-lookup"><span data-stu-id="167a4-179">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>  
  
 <span data-ttu-id="167a4-180">Chcete-li zajistit, že budou kompatibilní s budoucí serializace moduly typu, postupujte podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="167a4-180">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>  
  
- <span data-ttu-id="167a4-181">Vždycky nastavený **VersionAdded** vlastnost **OptionalFieldAttribute** atribut správně.</span><span class="sxs-lookup"><span data-stu-id="167a4-181">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>  
  
- <span data-ttu-id="167a4-182">Vyhněte se větvenou správy verzí.</span><span class="sxs-lookup"><span data-stu-id="167a4-182">Avoid branched versioning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167a4-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="167a4-183">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="167a4-184">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="167a4-184">Binary Serialization</span></span>](binary-serialization.md)
