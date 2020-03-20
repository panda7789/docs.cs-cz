---
title: Zabezpečení přístupu k metodě
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181148"
---
# <a name="securing-method-access"></a><span data-ttu-id="355eb-102">Zabezpečení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="355eb-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="355eb-103">Některé metody nemusí být vhodné pro povolení volání libovolného nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="355eb-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="355eb-104">Tyto metody představují několik rizik: Metoda může poskytnout některé omezené informace; mohlo by věřit, že jí byly předány jakékoli informace; nemusí provést kontrolu chyb na parametrech; nebo se špatnými parametry, může dojít k poruše nebo dělat něco škodlivého.</span><span class="sxs-lookup"><span data-stu-id="355eb-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="355eb-105">Měli byste si být vědomi těchto případů a přijmout opatření k ochraně metody.</span><span class="sxs-lookup"><span data-stu-id="355eb-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="355eb-106">V některých případech může být nutné omezit metody, které nejsou určeny pro veřejné použití, ale stále musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="355eb-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="355eb-107">Můžete mít například rozhraní, které musí být voláno napříč vlastními knihovnami DLL, a proto musí být veřejné, ale nechcete jej veřejně vystavit, abyste zabránili zákazníkům v jeho používání nebo aby škodlivý kód nemohl zneužívat vstupní bod do komponenty.</span><span class="sxs-lookup"><span data-stu-id="355eb-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="355eb-108">Dalším běžným důvodem k omezení metody, která není určena pro veřejné použití (ale musí být veřejná), je vyhnout se nutnosti dokumentovat a podporovat to, co může být velmi interní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="355eb-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="355eb-109">Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodám:</span><span class="sxs-lookup"><span data-stu-id="355eb-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="355eb-110">Omezte rozsah usnadnění pro třídu, sestavení nebo odvozené třídy, pokud mohou být důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="355eb-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="355eb-111">Toto je nejjednodušší způsob, jak omezit přístup k metodě.</span><span class="sxs-lookup"><span data-stu-id="355eb-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="355eb-112">Všimněte si, že obecně odvozené třídy může být méně důvěryhodné než třídy, které jsou odvozeny z, i když v některých případech sdílejí identitu nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="355eb-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="355eb-113">Zejména neodvodit důvěru z **klíčového**slova chráněné , který není nutně použit v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="355eb-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="355eb-114">Omezte přístup metody volajícím zadané identity – v podstatě všechny konkrétní [důkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatel, zóna a tak dále), které zvolíte.</span><span class="sxs-lookup"><span data-stu-id="355eb-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="355eb-115">Omezte přístup metody k volajícím, kteří mají jakákoli oprávnění, která vyberete.</span><span class="sxs-lookup"><span data-stu-id="355eb-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="355eb-116">Podobně deklarativní zabezpečení umožňuje řídit dědičnost tříd.</span><span class="sxs-lookup"><span data-stu-id="355eb-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="355eb-117">Můžete použít **InheritanceDemand** provést následující:</span><span class="sxs-lookup"><span data-stu-id="355eb-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="355eb-118">Vyžadovat odvozené třídy mít zadanou identitu nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="355eb-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="355eb-119">Vyžadovat odvozené třídy, které přepíší určité metody, aby měly zadanou identitu nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="355eb-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="355eb-120">Následující příklad ukazuje, jak pomoci chránit veřejnou třídu pro omezený přístup tím, že vyžaduje, aby volající být podepsány s určitým silným názvem.</span><span class="sxs-lookup"><span data-stu-id="355eb-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="355eb-121">Tento příklad <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> používá s **Demand pro** silný název.</span><span class="sxs-lookup"><span data-stu-id="355eb-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="355eb-122">Informace o tom, jak podepsat sestavení se silným názvem, naleznete v tématu [Vytváření a používání sestavení se silným názvem](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="355eb-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="355eb-123">Vyloučení tříd a členů z použití nedůvěryhodným kódem</span><span class="sxs-lookup"><span data-stu-id="355eb-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="355eb-124">Pomocí deklarací uvedených v této části můžete zabránit použití určitých tříd a metod, vlastností a událostí částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="355eb-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="355eb-125">Použitím těchto deklarací na třídu použijete ochranu na všechny její metody, vlastnosti a události; upozorňujeme však, že přístup k polím není deklarativním zabezpečením ovlivněn.</span><span class="sxs-lookup"><span data-stu-id="355eb-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="355eb-126">Všimněte si také, že požadavky na propojení pomáhají chránit pouze před bezprostředními volajícími a mohou být stále předmětem lákavých útoků.</span><span class="sxs-lookup"><span data-stu-id="355eb-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="355eb-127">Nový model transparentnosti byl zaveden v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="355eb-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="355eb-128">[Transparentní kód zabezpečení,](security-transparent-code-level-2.md) model úrovně 2 identifikuje <xref:System.Security.SecurityCriticalAttribute> zabezpečený kód s atributem.</span><span class="sxs-lookup"><span data-stu-id="355eb-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="355eb-129">Kód kritický pro zabezpečení vyžaduje, aby volající i dědicové byli plně důvěryhodní.</span><span class="sxs-lookup"><span data-stu-id="355eb-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="355eb-130">Sestavení spuštěná pod pravidly zabezpečení přístupu kódu z dřívějších verzí rozhraní .NET Framework mohou volat sestavení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="355eb-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="355eb-131">V takovém případě budou atributy kritické pro zabezpečení považovány za požadavky na propojení pro úplnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="355eb-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="355eb-132">V sestaveních se silným názvem [linkdemand](link-demands.md) je použita pro všechny veřejně přístupné metody, vlastnosti a události v něm omezit jejich použití plně důvěryhodných volajících.</span><span class="sxs-lookup"><span data-stu-id="355eb-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="355eb-133">Chcete-li tuto funkci zakázat, je nutné použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="355eb-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="355eb-134">Proto explicitně označení třídy vyloučit nedůvěryhodné volající je nezbytné pouze pro nepodepsané sestavení nebo sestavení s tímto atributem; tyto deklarace můžete označit podmnožinu typů v něm, které nejsou určeny pro nedůvěryhodné volající.</span><span class="sxs-lookup"><span data-stu-id="355eb-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="355eb-135">Následující příklady ukazují, jak zabránit tomu, aby třídy a členové používali nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="355eb-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="355eb-136">Pro veřejné nezapečetěné třídy:</span><span class="sxs-lookup"><span data-stu-id="355eb-136">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="355eb-137">Pro veřejné zapečetěné třídy:</span><span class="sxs-lookup"><span data-stu-id="355eb-137">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="355eb-138">Pro veřejné abstraktní třídy:</span><span class="sxs-lookup"><span data-stu-id="355eb-138">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="355eb-139">Pro veřejné virtuální funkce:</span><span class="sxs-lookup"><span data-stu-id="355eb-139">For public virtual functions:</span></span>  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="355eb-140">Pro veřejné abstraktní funkce:</span><span class="sxs-lookup"><span data-stu-id="355eb-140">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="355eb-141">Pro veřejné přepsat funkce, kde základní třída nevyžaduje úplný vztah důvěryhodnosti:</span><span class="sxs-lookup"><span data-stu-id="355eb-141">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="355eb-142">Pro veřejné přepsat funkce, kde základní třída vyžaduje plnou důvěryhodnost:</span><span class="sxs-lookup"><span data-stu-id="355eb-142">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="355eb-143">Pro veřejná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="355eb-143">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="355eb-144">Virtuální interní přepisy nebo přetížení přepsatelného přítele</span><span class="sxs-lookup"><span data-stu-id="355eb-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="355eb-145">Tato část varuje o problému se zabezpečením `virtual` `internal` při`Overloads` `Overridable` `Friend` deklarování metody jako oba a ( v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="355eb-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="355eb-146">Toto upozornění platí pouze pro rozhraní .NET Framework verze 1.0 a 1.1, nevztahuje se na novější verze.</span><span class="sxs-lookup"><span data-stu-id="355eb-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="355eb-147">V rozhraní .NET Framework verze 1.0 a 1.1, musíte být vědomi nuance přístupnosti systému typu při potvrzování, že váš kód není k dispozici pro jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="355eb-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="355eb-148">Metoda, která je deklarována **virtuální** a **interní** **(Přetížení overridable Friend** v jazyce Visual Basic) může přepsat položku vtable nadřazené třídy a lze ji použít pouze ze stejného sestavení, protože je interní.</span><span class="sxs-lookup"><span data-stu-id="355eb-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="355eb-149">Přístupnost pro přepsání je však určena **virtuální** klíčové slovo a to může být přepsána z jiného sestavení tak dlouho, dokud tento kód má přístup k samotné třídy.</span><span class="sxs-lookup"><span data-stu-id="355eb-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="355eb-150">Pokud možnost přepsání představuje problém, použijte deklarativní zabezpečení opravit nebo odebrat **virtuální** klíčové slovo, pokud není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="355eb-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="355eb-151">Všimněte si, že i v případě, že kompilátor jazyka brání tyto přepsání s chybou kompilace, je možné pro kód napsaný s jinými kompilátory přepsat.</span><span class="sxs-lookup"><span data-stu-id="355eb-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="355eb-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="355eb-152">See also</span></span>

- [<span data-ttu-id="355eb-153">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="355eb-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
