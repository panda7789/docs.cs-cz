---
title: Vlastní serializace
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
ms.openlocfilehash: 60fdc0317975d94433401e3214953b77d0970f60
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741055"
---
# <a name="custom-serialization"></a><span data-ttu-id="1aa7f-102">Vlastní serializace</span><span class="sxs-lookup"><span data-stu-id="1aa7f-102">Custom serialization</span></span>
<span data-ttu-id="1aa7f-103">Vlastní serializace je proces řízení serializace a deserializace typu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="1aa7f-104">Řízením serializace je možné zajistit kompatibilitu serializace, což je schopnost serializace a deserializace mezi verzemi typu bez narušení základní funkce typu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="1aa7f-105">Například v první verzi typu, může existovat pouze dvě pole.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="1aa7f-106">V příští verzi typu jsou přidány několik více polí.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="1aa7f-107">Ještě druhý verze aplikace, musí mít k serializaci a deserializaci oba typy.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="1aa7f-108">Níže uvedené části popisují, jak řídit serializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="1aa7f-109">Ve verzích starších než .NET Framework 4,0 bylo provedeno serializace vlastních uživatelských dat v částečně důvěryhodném sestavení pomocí GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="1aa7f-110">Počínaje verzí 4.0, která metoda je označena <xref:System.Security.SecurityCriticalAttribute> atributů, což zabrání spouštění v částečně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="1aa7f-111">Chcete-li vyřešit tuto podmínku, implementovat <xref:System.Runtime.Serialization.ISafeSerializationData> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="1aa7f-112">Spouštění vlastních metod během a po serializaci</span><span class="sxs-lookup"><span data-stu-id="1aa7f-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="1aa7f-113">Doporučeným postupem a jednoduchý způsob, jak (zavedeno ve verzi 2.0 rozhraní .NET Framework) se mají být použity následující atributy metody, které se používají k odstranění dat během a po serializace:</span><span class="sxs-lookup"><span data-stu-id="1aa7f-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="1aa7f-114">Tyto atributy umožňují typ k účasti v jedné z nebo všechny čtyři fází procesů serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="1aa7f-115">Atributy určují metody typu, který má být volána v každé fázi.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="1aa7f-116">Metody není přístup k datový proud serializace, ale místo toho bylo možné změnit objekt před a po serializaci, nebo před a po deserializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="1aa7f-117">Atributy lze použít na všech úrovních hierarchie dědičnosti typů a každá metoda je volána v hierarchii z základní k nejvíce odvozené.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="1aa7f-118">Tento mechanismus zabraňuje složitost a všechny výsledné problémy provádění <xref:System.Runtime.Serialization.ISerializable> rozhraní tím, že odpovědnost za serializace a deserializace za účelem implementace Většina odvozených.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="1aa7f-119">Kromě toho tento mechanismus umožňuje formátovací moduly, ignorovat naplnění polí a načtení z datový proud serializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="1aa7f-120">Podrobnosti a příklady řízení serializace a deserializace klikněte na tlačítko Předchozí odkazy.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="1aa7f-121">Kromě toho při přidávání nového pole na existující serializovatelný typ., použije <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na pole.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="1aa7f-122"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje absenci pole při zpracování datový proud, který chybí nové pole.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="1aa7f-123">Implementace rozhraní ISerializable</span><span class="sxs-lookup"><span data-stu-id="1aa7f-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="1aa7f-124">Druhý způsob, jak řídit serializaci, je dosaženo implementací rozhraní <xref:System.Runtime.Serialization.ISerializable> pro objekt.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="1aa7f-125">Upozorňujeme však, že metoda v předchozím oddílu nahrazuje tuto metodu za účelem serializace ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="1aa7f-126">Kromě toho byste neměli používat výchozí serializaci pro třídu, která je označena atributem [serializovatelný](xref:System.SerializableAttribute) a má deklarativní nebo imperativní zabezpečení na úrovni třídy nebo na konstruktorech.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="1aa7f-127">Namísto toho měli vždy implementovat tyto třídy <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="1aa7f-128">Implementace <xref:System.Runtime.Serialization.ISerializable> zahrnuje implementaci metody `GetObjectData` a speciální konstruktor, který se používá, pokud je objekt deserializován.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="1aa7f-129">Následující ukázkový kód ukazuje, jak implementovat <xref:System.Runtime.Serialization.ISerializable> na `MyObject` třídy z předchozího oddílu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
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
  
 <span data-ttu-id="1aa7f-130">Když je během serializace volána metoda **GetObjectData** , zodpovídáte za plnění <xref:System.Runtime.Serialization.SerializationInfo> poskytovaných voláním metody.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="1aa7f-131">Přidáte proměnné mají být serializován jako dvojice název a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="1aa7f-132">Libovolný text, lze použít jako název.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-132">Any text can be used as the name.</span></span> <span data-ttu-id="1aa7f-133">Máte svobodu rozhodnutí, které členské proměnné jsou přidány do <xref:System.Runtime.Serialization.SerializationInfo>, za předpokladu, že serializován dostatek dat. Chcete-li obnovit během deserializace objektu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="1aa7f-134">Odvozené třídy by měly volat metodu **GetObjectData** na základním objektu, pokud druhá implementuje <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="1aa7f-135">Všimněte si, že serializace může povolit další kódu zobrazit nebo upravit data instance objektu, který je jinak nedostupný.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="1aa7f-136">Proto kód, který provádí serializaci, vyžaduje [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) se zadaným příznakem <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter>.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="1aa7f-137">Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="1aa7f-138">Metoda **GetObjectData** musí být explicitně chráněna buď tak, že podává [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) se zadaným příznakem <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> nebo je náročné na jiná oprávnění, která specificky pomůžou chránit privátní data.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="1aa7f-139">Pokud soukromé pole ukládá citlivé informace, měli byste na **GetObjectData** vyžadovat příslušná oprávnění k ochraně dat.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="1aa7f-140">Pamatujte, že kód, který má přiřazenou [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) se zadaným příznakem **SerializationFormatter** , může zobrazit a upravit data uložená v soukromých polích.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="1aa7f-141">Škodlivý volající, který má tato [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) udělena, může zobrazit data, jako jsou skrytá adresářová umístění nebo udělit oprávnění, a používat je k zneužití ohrožení zabezpečení v počítači.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="1aa7f-142">Úplný seznam příznaků oprávnění zabezpečení, které můžete zadat, najdete v tématu [výčet SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="1aa7f-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="1aa7f-143">Je důležité zdůraznit, že při přidání <xref:System.Runtime.Serialization.ISerializable> do třídy je nutné implementovat jak **GetObjectData** , tak speciální konstruktor.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="1aa7f-144">Kompilátor vás upozorní, pokud **GetObjectData** chybí.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="1aa7f-145">Protože je nelze vynutit provádění konstruktor, bez upozornění je však k dispozici pokud chybí konstruktor a je vyvolána výjimka, pokud je proveden pokus o deserializaci třídy bez konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="1aa7f-146">Aktuální návrh byl podporuje výše <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodu za účelem získání kolem potenciální problémy zabezpečení a správy verzí.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="1aa7f-147">Například metoda `SetObjectData` musí být veřejná, pokud je definována jako součást rozhraní; Proto musí uživatelé napsat kód pro obranu před tím, než je metoda **SetObjectData** volána víckrát.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="1aa7f-148">Jinak škodlivá aplikace, která volá metodu **SetObjectData** na objektu v procesu provádění operace, může způsobit potenciální problémy.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="1aa7f-149">Během deserializace <xref:System.Runtime.Serialization.SerializationInfo> je předán do třídy pomocí konstruktoru určených k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="1aa7f-150">Omezeními viditelnost umístí na konstruktoru jsou ignorovány, pokud je objekt deserializován; Třída tak můžete označit jako veřejné, chráněný, interní nebo privátní.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="1aa7f-151">Je však osvědčeným postupem zajistit konstruktoru chráněný, pokud zapečetěné třídy v takovém případě by měla být konstruktoru označena privátní.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="1aa7f-152">Konstruktor by měl také provést důkladné ověření vstupu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="1aa7f-153">Chcete-li předejít zneužití škodlivým kódem, by měl konstruktoru vynutit stejné kontroly zabezpečení a oprávnění nutná k získání instance třídy pomocí jiných konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="1aa7f-154">Pokud toto doporučení neprovedete, škodlivý kód může předkonstruovat objekt, získat řízení [s použitím](xref:System.Security.Permissions.SecurityPermissionAttribute) příznaku <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> zadaného a deserializovat objekt v klientském počítači obejít jakékoli zabezpečení, které by bylo použito během konstrukce standardní instance pomocí veřejného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="1aa7f-155">Chcete-li obnovit stav objektu, jednoduše načíst hodnoty proměnných z <xref:System.Runtime.Serialization.SerializationInfo> pomocí názvů používat během serializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="1aa7f-156">Pokud je základní třída implementuje <xref:System.Runtime.Serialization.ISerializable>, by měla být volána konstruktor základní třídy, aby umožnila základní objekt, který chcete obnovit své proměnné.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="1aa7f-157">Při odvozování nové třídy z jednoho, který implementuje <xref:System.Runtime.Serialization.ISerializable>, musí odvozená třída implementovat konstruktor i metodu **GetObjectData** , pokud má proměnné, které je třeba serializovat.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="1aa7f-158">Následující příklad kódu ukazuje, jak to lze provést pomocí `MyObject` třídy, které jsou uvedeny dříve.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
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
  
 <span data-ttu-id="1aa7f-159">Nezapomeňte volat základní třídu v konstruktoru deserializace.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="1aa7f-160">Není-li toto provedeno, konstruktor základní třídy se nikdy nevolá a objekt není po deserializaci plně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="1aa7f-161">Objekty jsou znovu vytvořena zevnitř a volání metod během deserializace může mít nežádoucí vedlejší účinky, protože volání metody může odkazovat na objekt odkazy, které nebyly byla deserializovat o dobu, kterou při volání.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="1aa7f-162">Pokud deserializovaná třída implementuje <xref:System.Runtime.Serialization.IDeserializationCallback>, metoda <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> je automaticky volána, když byl deserializován celý graf objektu.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="1aa7f-163">V tomto okamžiku byly plně obnoveny všechny podřízené objekty odkazuje.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="1aa7f-164">Tabulka hash je typickým příkladem třídu, která je obtížné deserializaci bez použití naslouchací proces události.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="1aa7f-165">Vše je snadné k načtení dvojice klíč a hodnotu během deserializace, ale přidáním těchto objektů zpět do tabulky algoritmu hash může způsobit problémy vzhledem k tomu, že neexistuje žádná záruka této třídy, které odvozen z tabulky hash deserializovat.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="1aa7f-166">Volání metod z tabulky hash v této fázi není proto doporučuje.</span><span class="sxs-lookup"><span data-stu-id="1aa7f-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa7f-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1aa7f-167">See also</span></span>

- [<span data-ttu-id="1aa7f-168">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="1aa7f-168">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="1aa7f-169">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="1aa7f-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="1aa7f-170">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="1aa7f-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
