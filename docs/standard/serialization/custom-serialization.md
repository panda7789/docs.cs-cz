---
title: Vlastní serializace
description: Vlastní serializace řídí serializaci a deserializaci typu. Řízení serializace může zajistit kompatibilitu serializace.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: dcd5fa2777d2f1e351179570806a95eb835ad843
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375998"
---
# <a name="custom-serialization"></a><span data-ttu-id="03f36-104">Vlastní serializace</span><span class="sxs-lookup"><span data-stu-id="03f36-104">Custom serialization</span></span>
<span data-ttu-id="03f36-105">Vlastní serializace je proces řízení serializace a deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="03f36-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="03f36-106">Řízením serializace je možné zajistit kompatibilitu serializace, což je schopnost serializace a deserializace mezi verzemi typu bez narušení základní funkce typu.</span><span class="sxs-lookup"><span data-stu-id="03f36-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="03f36-107">Například v první verzi typu, může existovat pouze dvě pole.</span><span class="sxs-lookup"><span data-stu-id="03f36-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="03f36-108">V příští verzi typu jsou přidány několik více polí.</span><span class="sxs-lookup"><span data-stu-id="03f36-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="03f36-109">Ještě druhý verze aplikace, musí mít k serializaci a deserializaci oba typy.</span><span class="sxs-lookup"><span data-stu-id="03f36-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="03f36-110">Níže uvedené části popisují, jak řídit serializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="03f36-111">Ve verzích starších než .NET Framework 4,0 bylo provedeno serializace vlastních uživatelských dat v částečně důvěryhodném sestavení pomocí GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="03f36-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="03f36-112">Počínaje verzí 4.0, která metoda je označena <xref:System.Security.SecurityCriticalAttribute> atributů, což zabrání spouštění v částečně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="03f36-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="03f36-113">Chcete-li vyřešit tuto podmínku, implementovat <xref:System.Runtime.Serialization.ISafeSerializationData> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03f36-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="03f36-114">Spouštění vlastních metod během a po serializaci</span><span class="sxs-lookup"><span data-stu-id="03f36-114">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="03f36-115">Doporučeným postupem a jednoduchý způsob, jak (zavedeno ve verzi 2.0 rozhraní .NET Framework) se mají být použity následující atributy metody, které se používají k odstranění dat během a po serializace:</span><span class="sxs-lookup"><span data-stu-id="03f36-115">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="03f36-116">Tyto atributy umožňují typ k účasti v jedné z nebo všechny čtyři fází procesů serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="03f36-117">Atributy určují metody typu, který má být volána v každé fázi.</span><span class="sxs-lookup"><span data-stu-id="03f36-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="03f36-118">Metody není přístup k datový proud serializace, ale místo toho bylo možné změnit objekt před a po serializaci, nebo před a po deserializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="03f36-119">Atributy lze použít na všech úrovních hierarchie dědičnosti typů a každá metoda je volána v hierarchii z základní k nejvíce odvozené.</span><span class="sxs-lookup"><span data-stu-id="03f36-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="03f36-120">Tento mechanismus zabraňuje složitost a všechny výsledné problémy provádění <xref:System.Runtime.Serialization.ISerializable> rozhraní tím, že odpovědnost za serializace a deserializace za účelem implementace Většina odvozených.</span><span class="sxs-lookup"><span data-stu-id="03f36-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="03f36-121">Kromě toho tento mechanismus umožňuje formátovací moduly, ignorovat naplnění polí a načtení z datový proud serializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="03f36-122">Podrobnosti a příklady řízení serializace a deserializace klikněte na tlačítko Předchozí odkazy.</span><span class="sxs-lookup"><span data-stu-id="03f36-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="03f36-123">Kromě toho při přidávání nového pole na existující serializovatelný typ., použije <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na pole.</span><span class="sxs-lookup"><span data-stu-id="03f36-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="03f36-124"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje absenci pole při zpracování datový proud, který chybí nové pole.</span><span class="sxs-lookup"><span data-stu-id="03f36-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="03f36-125">Implementace rozhraní ISerializable</span><span class="sxs-lookup"><span data-stu-id="03f36-125">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="03f36-126">Druhý způsob, jak řídit serializaci, je dosaženo implementací <xref:System.Runtime.Serialization.ISerializable> rozhraní objektu.</span><span class="sxs-lookup"><span data-stu-id="03f36-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="03f36-127">Upozorňujeme však, že metoda v předchozím oddílu nahrazuje tuto metodu za účelem serializace ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="03f36-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="03f36-128">Kromě toho byste neměli používat výchozí serializaci pro třídu, která je označena atributem [serializovatelný](xref:System.SerializableAttribute) a má deklarativní nebo imperativní zabezpečení na úrovni třídy nebo na konstruktorech.</span><span class="sxs-lookup"><span data-stu-id="03f36-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="03f36-129">Namísto toho měli vždy implementovat tyto třídy <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03f36-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="03f36-130">Implementace <xref:System.Runtime.Serialization.ISerializable> zahrnuje implementaci `GetObjectData` metody a speciální konstruktor, který se používá, pokud je objekt deserializován.</span><span class="sxs-lookup"><span data-stu-id="03f36-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="03f36-131">Následující ukázkový kód ukazuje, jak implementovat <xref:System.Runtime.Serialization.ISerializable> na `MyObject` třídy z předchozího oddílu.</span><span class="sxs-lookup"><span data-stu-id="03f36-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="03f36-132">Když je během serializace volána metoda **GetObjectData** , zodpovídáte za naplnění <xref:System.Runtime.Serialization.SerializationInfo> poskytované voláním metody.</span><span class="sxs-lookup"><span data-stu-id="03f36-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="03f36-133">Přidáte proměnné mají být serializován jako dvojice název a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="03f36-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="03f36-134">Libovolný text, lze použít jako název.</span><span class="sxs-lookup"><span data-stu-id="03f36-134">Any text can be used as the name.</span></span> <span data-ttu-id="03f36-135">Máte svobodu rozhodnutí, které členské proměnné jsou přidány do <xref:System.Runtime.Serialization.SerializationInfo>, za předpokladu, že serializován dostatek dat. Chcete-li obnovit během deserializace objektu.</span><span class="sxs-lookup"><span data-stu-id="03f36-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="03f36-136">Odvozené třídy by měly volat metodu **GetObjectData** na základním objektu, pokud druhá implementuje <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="03f36-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="03f36-137">Všimněte si, že serializace může povolit další kódu zobrazit nebo upravit data instance objektu, který je jinak nedostupný.</span><span class="sxs-lookup"><span data-stu-id="03f36-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="03f36-138">Proto kód, který provádí serializaci, vyžaduje [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) se <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> zadaným příznakem.</span><span class="sxs-lookup"><span data-stu-id="03f36-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="03f36-139">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="03f36-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="03f36-140">Metoda **GetObjectData** musí být explicitně chráněna buď tak, že [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> podává SecurityPermission se zadaným příznakem, nebo je náročné na jiná oprávnění, která specificky pomůžou chránit privátní data.</span><span class="sxs-lookup"><span data-stu-id="03f36-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="03f36-141">Pokud soukromé pole ukládá citlivé informace, měli byste na **GetObjectData** vyžadovat příslušná oprávnění k ochraně dat.</span><span class="sxs-lookup"><span data-stu-id="03f36-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="03f36-142">Pamatujte, že kód, který má přiřazenou [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) se zadaným příznakem **SerializationFormatter** , může zobrazit a upravit data uložená v soukromých polích.</span><span class="sxs-lookup"><span data-stu-id="03f36-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="03f36-143">Škodlivý volající, který má tato [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) udělena, může zobrazit data, jako jsou skrytá adresářová umístění nebo udělit oprávnění, a používat je k zneužití ohrožení zabezpečení v počítači.</span><span class="sxs-lookup"><span data-stu-id="03f36-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="03f36-144">Úplný seznam příznaků oprávnění zabezpečení, které můžete zadat, najdete v tématu [výčet SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="03f36-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="03f36-145">Je důležité zdůraznit, že při <xref:System.Runtime.Serialization.ISerializable> přidání do třídy je nutné implementovat jak **GetObjectData** , tak speciální konstruktor.</span><span class="sxs-lookup"><span data-stu-id="03f36-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="03f36-146">Kompilátor vás upozorní, pokud **GetObjectData** chybí.</span><span class="sxs-lookup"><span data-stu-id="03f36-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="03f36-147">Protože je nelze vynutit provádění konstruktor, bez upozornění je však k dispozici pokud chybí konstruktor a je vyvolána výjimka, pokud je proveden pokus o deserializaci třídy bez konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="03f36-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="03f36-148">Aktuální návrh byl podporuje výše <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodu za účelem získání kolem potenciální problémy zabezpečení a správy verzí.</span><span class="sxs-lookup"><span data-stu-id="03f36-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="03f36-149">Například `SetObjectData` Metoda musí být veřejná, pokud je definována jako součást rozhraní; proto musí uživatelé napsat kód pro obranu před tím, než je metoda **SetObjectData** volána víckrát.</span><span class="sxs-lookup"><span data-stu-id="03f36-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="03f36-150">Jinak škodlivá aplikace, která volá metodu **SetObjectData** na objektu v procesu provádění operace, může způsobit potenciální problémy.</span><span class="sxs-lookup"><span data-stu-id="03f36-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="03f36-151">Během deserializace <xref:System.Runtime.Serialization.SerializationInfo> je předán do třídy pomocí konstruktoru určených k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="03f36-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="03f36-152">Omezeními viditelnost umístí na konstruktoru jsou ignorovány, pokud je objekt deserializován; Třída tak můžete označit jako veřejné, chráněný, interní nebo privátní.</span><span class="sxs-lookup"><span data-stu-id="03f36-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="03f36-153">Je však osvědčeným postupem zajistit konstruktoru chráněný, pokud zapečetěné třídy v takovém případě by měla být konstruktoru označena privátní.</span><span class="sxs-lookup"><span data-stu-id="03f36-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="03f36-154">Konstruktor by měl také provést důkladné ověření vstupu.</span><span class="sxs-lookup"><span data-stu-id="03f36-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="03f36-155">Chcete-li předejít zneužití škodlivým kódem, by měl konstruktoru vynutit stejné kontroly zabezpečení a oprávnění nutná k získání instance třídy pomocí jiných konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="03f36-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="03f36-156">Pokud toto doporučení neprovedete, škodlivý kód může předkonstruovat objekt, získat řízení [s použitím](xref:System.Security.Permissions.SecurityPermissionAttribute) <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> příznaku a deserializovat objekt v klientském počítači obejít jakékoli zabezpečení, které by bylo použito během konstrukce standardní instance pomocí veřejného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="03f36-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="03f36-157">Chcete-li obnovit stav objektu, jednoduše načíst hodnoty proměnných z <xref:System.Runtime.Serialization.SerializationInfo> pomocí názvů používat během serializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="03f36-158">Pokud je základní třída implementuje <xref:System.Runtime.Serialization.ISerializable>, by měla být volána konstruktor základní třídy, aby umožnila základní objekt, který chcete obnovit své proměnné.</span><span class="sxs-lookup"><span data-stu-id="03f36-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="03f36-159">Při odvozování nové třídy z rozhraní, které implementuje <xref:System.Runtime.Serialization.ISerializable> , musí odvozená třída implementovat konstruktor i metodu **GetObjectData** , pokud má proměnné, které musí být serializovány.</span><span class="sxs-lookup"><span data-stu-id="03f36-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="03f36-160">Následující příklad kódu ukazuje, jak to lze provést pomocí `MyObject` třídy, které jsou uvedeny dříve.</span><span class="sxs-lookup"><span data-stu-id="03f36-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="03f36-161">Nezapomeňte volat základní třídu v konstruktoru deserializace.</span><span class="sxs-lookup"><span data-stu-id="03f36-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="03f36-162">Není-li toto provedeno, konstruktor základní třídy se nikdy nevolá a objekt není po deserializaci plně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="03f36-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="03f36-163">Objekty jsou znovu vytvořena zevnitř a volání metod během deserializace může mít nežádoucí vedlejší účinky, protože volání metody může odkazovat na objekt odkazy, které nebyly byla deserializovat o dobu, kterou při volání.</span><span class="sxs-lookup"><span data-stu-id="03f36-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="03f36-164">Pokud deserializovaná třída implementuje <xref:System.Runtime.Serialization.IDeserializationCallback> , <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> Metoda je automaticky volána, když je celý graf objektů deserializován.</span><span class="sxs-lookup"><span data-stu-id="03f36-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="03f36-165">V tomto okamžiku byly plně obnoveny všechny podřízené objekty odkazuje.</span><span class="sxs-lookup"><span data-stu-id="03f36-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="03f36-166">Tabulka hash je typickým příkladem třídu, která je obtížné deserializaci bez použití naslouchací proces události.</span><span class="sxs-lookup"><span data-stu-id="03f36-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="03f36-167">Vše je snadné k načtení dvojice klíč a hodnotu během deserializace, ale přidáním těchto objektů zpět do tabulky algoritmu hash může způsobit problémy vzhledem k tomu, že neexistuje žádná záruka této třídy, které odvozen z tabulky hash deserializovat.</span><span class="sxs-lookup"><span data-stu-id="03f36-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="03f36-168">Volání metod z tabulky hash v této fázi není proto doporučuje.</span><span class="sxs-lookup"><span data-stu-id="03f36-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f36-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="03f36-169">See also</span></span>

- [<span data-ttu-id="03f36-170">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="03f36-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="03f36-171">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="03f36-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="03f36-172">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="03f36-172">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
