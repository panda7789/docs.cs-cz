---
title: Serializace odolná proti verzi
description: .NET Framework 2,0 zavádí serializaci odolnou proti verzím, sadu funkcí, které usnadňují úpravu serializovatelných typů.
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
ms.openlocfilehash: afc822e1f8873bac069f6634fdf1d4665d392e69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762588"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="02ffe-103">Serializace odolná proti verzi</span><span class="sxs-lookup"><span data-stu-id="02ffe-103">Version tolerant serialization</span></span>

<span data-ttu-id="02ffe-104">Ve verzi 1.0 a 1.1 rozhraní .NET Framework byla problematický vytváření Serializovatelné typy, které by se znovu použít z jedné verze aplikace na další.</span><span class="sxs-lookup"><span data-stu-id="02ffe-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="02ffe-105">V případě typu byl změněn přidáním pole navíc, by se objeví následující problémy:</span><span class="sxs-lookup"><span data-stu-id="02ffe-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="02ffe-106">Starší verze aplikace by vyvolat výjimky dotaz k deserializaci nové verze původní typu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="02ffe-107">Novější verze aplikace by výjimku výjimky, při deserializaci starší verze typu s chybějící data.</span><span class="sxs-lookup"><span data-stu-id="02ffe-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="02ffe-108">Verze chybám serializace (VTS) je sada funkcí zavedena v rozhraní .NET Framework 2.0, který umožňuje snadněji v čase, chcete-li upravit Serializovatelné typy.</span><span class="sxs-lookup"><span data-stu-id="02ffe-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="02ffe-109">Konkrétně jsou povoleny funkce VTS pro třídy, do kterého <xref:System.SerializableAttribute> byl použit atribut, včetně obecných typů.</span><span class="sxs-lookup"><span data-stu-id="02ffe-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="02ffe-110">VTS umožňuje přidat nové pole do těchto tříd bez porušení kompatibilitu s jinými verzemi typu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="02ffe-111">Pracovní ukázkovou aplikaci najdete v tématu [ukázka technologie serializace odolného proti verzi](basic-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="02ffe-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="02ffe-112">Jsou povoleny funkce VTS, používáte-li <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="02ffe-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="02ffe-113">Navíc povoleny všechny funkce s výjimkou tolerance nadbytečná data také při použití <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="02ffe-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="02ffe-114">Další informace o použití těchto tříd pro serializaci naleznete v tématu [binární serializace](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="02ffe-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="02ffe-115">Seznam funkcí</span><span class="sxs-lookup"><span data-stu-id="02ffe-115">Feature list</span></span>

<span data-ttu-id="02ffe-116">Sada funkcí obsahuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="02ffe-116">The set of features includes the following:</span></span>

- <span data-ttu-id="02ffe-117">Odchylka nadbytečná nebo neočekávaná data.</span><span class="sxs-lookup"><span data-stu-id="02ffe-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="02ffe-118">To umožňuje novější verze tohoto typu k odesílání dat ke starším verzím.</span><span class="sxs-lookup"><span data-stu-id="02ffe-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="02ffe-119">Odchylka chybějících volitelnými daty.</span><span class="sxs-lookup"><span data-stu-id="02ffe-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="02ffe-120">To umožňuje starší verze k odesílání dat do novější verze.</span><span class="sxs-lookup"><span data-stu-id="02ffe-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="02ffe-121">Zpětná volání serializace.</span><span class="sxs-lookup"><span data-stu-id="02ffe-121">Serialization callbacks.</span></span> <span data-ttu-id="02ffe-122">To umožňuje inteligentní výchozí nastavení hodnoty v případech, kdy je chybějící data.</span><span class="sxs-lookup"><span data-stu-id="02ffe-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="02ffe-123">Kromě toho je funkce k prohlášení, pokud byl přidán nový volitelné pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="02ffe-124">Toto je <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> vlastnost <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="02ffe-125">Tyto funkce jsou podrobněji popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="02ffe-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="02ffe-126">Tolerance nadbytečná nebo neočekávaná data</span><span class="sxs-lookup"><span data-stu-id="02ffe-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="02ffe-127">Všechna nadbytečná nebo neočekávaná data v minulosti během deserializace způsobeno výjimky, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="02ffe-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="02ffe-128">S VTS ve stejné situaci, všechna nadbytečná nebo neočekávaná data, je ignorován namísto způsobující výjimky, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="02ffe-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="02ffe-129">To umožňuje aplikacím, které používají novější verze tohoto typu (to znamená, že verzi, která obsahuje více polí) k odeslání informací do aplikace, které očekávají starších verzích stejného typu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="02ffe-130">V následujícím příkladu doplňující data obsažená v `CountryField` verze 2.0 `Address` třída je ignorována, pokud starší aplikace deserializuje novější verzi.</span><span class="sxs-lookup"><span data-stu-id="02ffe-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

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

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="02ffe-131">Tolerance chybějících dat</span><span class="sxs-lookup"><span data-stu-id="02ffe-131">Tolerance of missing data</span></span>

<span data-ttu-id="02ffe-132">Pole může být označen jako volitelné použitím <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na ně.</span><span class="sxs-lookup"><span data-stu-id="02ffe-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="02ffe-133">Během deserializace nepovinné údaje chybí, je-li pro Serializační stroj ignoruje absenci a nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="02ffe-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="02ffe-134">Aplikace, které očekávají starší verze typu tedy můžete odeslat data aplikací, které očekáváte novější verze stejného typu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="02ffe-135">Následující příklad ukazuje, verze 2.0 `Address` třídy s `CountryField` pole označeno jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="02ffe-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="02ffe-136">Je-li starší aplikace odešle verze 1 a novější aplikace, která očekává verze 2.0, je ignorován neexistují data.</span><span class="sxs-lookup"><span data-stu-id="02ffe-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

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
  
### <a name="serialization-callbacks"></a><span data-ttu-id="02ffe-137">Zpětná volání serializace</span><span class="sxs-lookup"><span data-stu-id="02ffe-137">Serialization callbacks</span></span>

<span data-ttu-id="02ffe-138">Zpětná volání serializace jsou mechanismus, který poskytuje zachytávání do procesu serializaci nebo deserializaci na čtyři body.</span><span class="sxs-lookup"><span data-stu-id="02ffe-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="02ffe-139">Atribut</span><span class="sxs-lookup"><span data-stu-id="02ffe-139">Attribute</span></span>|<span data-ttu-id="02ffe-140">Když je volána metoda přidružené</span><span class="sxs-lookup"><span data-stu-id="02ffe-140">When the Associated Method is Called</span></span>|<span data-ttu-id="02ffe-141">Typické použití</span><span class="sxs-lookup"><span data-stu-id="02ffe-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="02ffe-142">Před deserializací.\*</span><span class="sxs-lookup"><span data-stu-id="02ffe-142">Before deserialization.\*</span></span>|<span data-ttu-id="02ffe-143">Inicializuje výchozí hodnoty pro volitelná pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="02ffe-144">Po deserializace.</span><span class="sxs-lookup"><span data-stu-id="02ffe-144">After deserialization.</span></span>|<span data-ttu-id="02ffe-145">Opravte hodnoty volitelné pole založené na obsahu další pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="02ffe-146">Před serializací.</span><span class="sxs-lookup"><span data-stu-id="02ffe-146">Before serialization.</span></span>|<span data-ttu-id="02ffe-147">Připravte pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="02ffe-147">Prepare for serialization.</span></span> <span data-ttu-id="02ffe-148">Můžete například vytvořte struktury volitelnými daty.</span><span class="sxs-lookup"><span data-stu-id="02ffe-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="02ffe-149">Po serializace.</span><span class="sxs-lookup"><span data-stu-id="02ffe-149">After serialization.</span></span>|<span data-ttu-id="02ffe-150">Protokolovat události serializace.</span><span class="sxs-lookup"><span data-stu-id="02ffe-150">Log serialization events.</span></span>|

 <span data-ttu-id="02ffe-151">\*Toto zpětné volání je vyvoláno před konstruktor deserializace, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02ffe-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="02ffe-152">Použití zpětných volání</span><span class="sxs-lookup"><span data-stu-id="02ffe-152">Using callbacks</span></span>

<span data-ttu-id="02ffe-153">Chcete-li použít zpětná volání, vztahují na metodu, která přijme příslušný atribut <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="02ffe-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="02ffe-154">Pouze jednu metodu na třídu může být označena každý z těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="02ffe-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="02ffe-155">Například:</span><span class="sxs-lookup"><span data-stu-id="02ffe-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="02ffe-156">Tyto metody slouží pro správu verzí.</span><span class="sxs-lookup"><span data-stu-id="02ffe-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="02ffe-157">Během deserializace volitelné pole nemusí být správně inicializován Pokud chybí data pro pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="02ffe-158">To lze opravit vytvořením metody, která přiřazuje správnou hodnotu, a poté použití atributu **OnDeserializingAttribute** nebo **OnDeserializedAttribute** na metodu.</span><span class="sxs-lookup"><span data-stu-id="02ffe-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="02ffe-159">Následující příklad ukazuje metodu v souvislosti s typem.</span><span class="sxs-lookup"><span data-stu-id="02ffe-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="02ffe-160">Je-li starší verzi aplikace odešle instanci `Address` třídy na novější verzi aplikace, `CountryField` pole data budou chybějící.</span><span class="sxs-lookup"><span data-stu-id="02ffe-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="02ffe-161">Ale po deserializaci bude pole nastavené na výchozí hodnotu "Japonsko".</span><span class="sxs-lookup"><span data-stu-id="02ffe-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
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
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="02ffe-162">Vlastnost VersionAdded</span><span class="sxs-lookup"><span data-stu-id="02ffe-162">The VersionAdded property</span></span>

<span data-ttu-id="02ffe-163">**OptionalFieldAttribute** má vlastnost **VersionAdded** .</span><span class="sxs-lookup"><span data-stu-id="02ffe-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="02ffe-164">Ve verzi 2,0 .NET Framework to není použito.</span><span class="sxs-lookup"><span data-stu-id="02ffe-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="02ffe-165">Je však důležité nastavit tuto vlastnost správně, aby bylo zajištěno, že bude typ kompatibilní s budoucími serializačními moduly.</span><span class="sxs-lookup"><span data-stu-id="02ffe-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="02ffe-166">Vlastnost určuje, kterou verzi typu bylo přidáno daného pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="02ffe-167">By měla být zvýšena podle právě jeden (počínaje 2) pokaždé, když je změněn na typ, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="02ffe-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

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

## <a name="serializationbinder"></a><span data-ttu-id="02ffe-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="02ffe-168">SerializationBinder</span></span>

<span data-ttu-id="02ffe-169">Někteří uživatelé muset které třídu k serializaci a deserializaci vzhledem k tomu, že u serverových a klientských je nutné zadat jinou verzi třídy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="02ffe-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="02ffe-170"><xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třída, která slouží k řízení skutečných typů použitých během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="02ffe-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="02ffe-171">Chcete-li použít tuto třídu, dosáhnout odvozením třídy od <xref:System.Runtime.Serialization.SerializationBinder> a přepište <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="02ffe-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="02ffe-172">Další informace naleznete v tématu [řízení serializace a deserializace pomocí SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="02ffe-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="02ffe-173">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="02ffe-173">Best practices</span></span>

<span data-ttu-id="02ffe-174">Chcete-li zajistit správnou verzí chování, postupujte podle těchto pravidel ke změně typu na verzi:</span><span class="sxs-lookup"><span data-stu-id="02ffe-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="02ffe-175">Serializovaná pole nikdy odebrat.</span><span class="sxs-lookup"><span data-stu-id="02ffe-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="02ffe-176">Nikdy použít <xref:System.NonSerializedAttribute> atributu na pole, pokud atribut nebyl použit na pole v předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="02ffe-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="02ffe-177">Nikdy změnit název nebo typ serializovaného pole.</span><span class="sxs-lookup"><span data-stu-id="02ffe-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="02ffe-178">Při přidávání nového serializovaného pole použijte atribut **OptionalFieldAttribute** .</span><span class="sxs-lookup"><span data-stu-id="02ffe-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="02ffe-179">Při odebírání atributu **NonSerializedAttribute** z pole (které nebylo serializovatelný v předchozí verzi) použijte atribut **OptionalFieldAttribute** .</span><span class="sxs-lookup"><span data-stu-id="02ffe-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="02ffe-180">U všech volitelných polí nastavte smysluplné výchozí hodnoty pomocí zpětných volání serializace, pokud nejsou povoleny výchozí hodnoty 0 nebo **null** .</span><span class="sxs-lookup"><span data-stu-id="02ffe-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="02ffe-181">Chcete-li zajistit, že budou kompatibilní s budoucí serializace moduly typu, postupujte podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="02ffe-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="02ffe-182">Vždy nastavte vlastnost **VersionAdded** u atributu **OptionalFieldAttribute** správně.</span><span class="sxs-lookup"><span data-stu-id="02ffe-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="02ffe-183">Vyhněte se větvenou správy verzí.</span><span class="sxs-lookup"><span data-stu-id="02ffe-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="02ffe-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="02ffe-184">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="02ffe-185">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="02ffe-185">Binary Serialization</span></span>](binary-serialization.md)
