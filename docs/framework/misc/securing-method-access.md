---
title: Zabezpečení přístupu k metodě
description: Naučte se zabezpečit přístup k metodám pro metody, které nejsou určené pro veřejné použití, ale pořád musí být veřejné.
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
ms.openlocfilehash: 88868ab29fc37854959a044b9c0fed5bd8c82d77
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855761"
---
# <a name="securing-method-access"></a><span data-ttu-id="cd3ab-103">Zabezpečení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="cd3ab-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="cd3ab-104">Některé metody nemusí být vhodné, aby bylo možné volat libovolný nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="cd3ab-105">Tyto metody představují několik rizik: metoda může poskytovat nějaké omezené informace; může se stát, že se budou předávat nějaké informace; nemusí provádět kontrolu chyb u parametrů; nebo s chybnými parametry může být nefunkční nebo něco škodlivého.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="cd3ab-106">Měli byste si být vědomi těchto případů a provést akci, která vám pomůžou ochránit tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="cd3ab-107">V některých případech možná budete muset omezit metody, které nejsou určené pro veřejné použití, ale pořád musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="cd3ab-108">Například můžete mít rozhraní, které je třeba volat napříč vašimi vlastními knihovnami DLL, a proto musí být veřejné, ale nechcete zveřejnit ho veřejně, aby se zabránilo zákazníkům v jeho použití, nebo aby se zabránilo škodlivému kódu v zneužití vstupního bodu do vaší komponenty.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="cd3ab-109">Dalším běžným důvodem pro omezení metody, která není určená pro veřejné použití (ale musí být veřejná), je vyhnout se nutnosti dokumentovat a podporovat to, co by mohlo být interní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="cd3ab-110">Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodě:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="cd3ab-111">Omezte rozsah dostupnosti pro třídu, sestavení nebo odvozené třídy, pokud mohou být důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="cd3ab-112">Toto je nejjednodušší způsob, jak omezit přístup k metodě.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="cd3ab-113">Obecně mohou být odvozené třídy méně důvěryhodné než třída odvozená z, i když v některých případech sdílí identitu nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="cd3ab-114">Konkrétně neodvozujte důvěryhodnost z klíčového slova `protected` , který není nutně použit v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="cd3ab-115">Omezte přístup k metodě u volajících zadané identity – v podstatě všechny konkrétní [legitimace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatel, zóna atd.) si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="cd3ab-116">Omezte přístup k metodě volajících, která mají jakákoli oprávnění, která jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="cd3ab-117">Podobně deklarativní zabezpečení umožňuje řídit dědičnost tříd.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="cd3ab-118">**InheritanceDemand** můžete použít k následujícím akcím:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="cd3ab-119">Vyžaduje, aby odvozené třídy měly zadanou identitu nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="cd3ab-120">Vyžadovat odvozené třídy, které přepíší konkrétní metody, aby měly zadanou identitu nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="cd3ab-121">Následující příklad ukazuje, jak přispět k ochraně veřejné třídy pro omezený přístup tím, že vyžaduje, aby volající byli podepsáni pomocí konkrétního silného názvu.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="cd3ab-122">Tento příklad používá <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> s **poptávkou** pro silný název.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="cd3ab-123">Informace o tom, jak podepsat sestavení se silným názvem, naleznete v tématu [vytváření a používání sestavení se silným názvem](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="cd3ab-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="cd3ab-124">Vyloučení tříd a členů z použití nedůvěryhodným kódem</span><span class="sxs-lookup"><span data-stu-id="cd3ab-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="cd3ab-125">Použijte deklarace uvedené v této části, chcete-li zabránit konkrétním třídám a metodám, a také k vlastnostem a událostem, od použití částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="cd3ab-126">Použitím těchto deklarací u třídy můžete použít ochranu na všechny metody, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="cd3ab-127">Přístup k poli však není ovlivněn deklarativním zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="cd3ab-128">Všimněte si také, že požadavky na propojení můžou chránit jenom před okamžitými volajícími a můžou se i nadále luring útoky.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd3ab-129">Nový model transparentnosti se zavedl do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="cd3ab-130">[Kód transparentní z hlediska zabezpečení, model úrovně 2,](security-transparent-code-level-2.md) identifikuje zabezpečený kód s <xref:System.Security.SecurityCriticalAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="cd3ab-131">Kód kritický pro zabezpečení vyžaduje, aby volající a dědice byly plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="cd3ab-132">Sestavení, která jsou spuštěna pod pravidly zabezpečení přístupu kódu z dřívějších .NET Framework verzí, mohou volat sestavení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="cd3ab-133">V takovém případě budou atributy kritické pro zabezpečení považovány za požadavky propojení pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="cd3ab-134">V sestavení se silným názvem je [LinkDemand](link-demands.md) použit pro všechny veřejně přístupné metody, vlastnosti a události v rámci omezení jejich použití pro plně důvěryhodné volající.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="cd3ab-135">Chcete-li tuto funkci zakázat, je nutné použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="cd3ab-136">Proto explicitní označení tříd pro vyloučení nedůvěryhodných volajících je nezbytné pouze pro nepodepsaná sestavení nebo sestavení s tímto atributem; Tyto deklarace lze použít k označení podmnožiny typů, které nejsou určeny pro nedůvěryhodné volající.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="cd3ab-137">Následující příklady ukazují, jak zabránit používání tříd a členů pomocí nedůvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="cd3ab-138">Pro veřejné nezapečetěné třídy:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-138">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-139">Pro veřejné zapečetěné třídy:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-139">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-140">Pro veřejné abstraktní třídy:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-140">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-141">Pro veřejné virtuální funkce:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-141">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-142">Pro veřejné abstraktní funkce:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-142">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-143">Pro veřejné funkce přepsání, kde základní třída nesplňuje požadavky na úplný vztah důvěryhodnosti:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-143">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-144">Pro veřejné funkce přepsání, kde základní třída požaduje úplný vztah důvěryhodnosti:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-144">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="cd3ab-145">Pro veřejná rozhraní:</span><span class="sxs-lookup"><span data-stu-id="cd3ab-145">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="cd3ab-146">Virtuální interní přepisy nebo přetížení přepsatelného přítele</span><span class="sxs-lookup"><span data-stu-id="cd3ab-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd3ab-147">V této části se dozvíte o potížích se zabezpečením při deklaraci metody jako obou `virtual` i `internal` ( `Overloads` `Overridable` `Friend` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cd3ab-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="cd3ab-148">Toto upozornění se vztahuje pouze na verze .NET Framework 1,0 a 1,1, ale nevztahuje se na novější verze.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="cd3ab-149">V .NET Framework verzích 1,0 a 1,1 je nutné znát nuance typu přístupnost systému při potvrzení, že váš kód není k dispozici jiným sestavením.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="cd3ab-150">Metoda, která je deklarována jako **Virtual** a **interní** (přepisovatelných**přátel** v Visual Basic) může přepsat položku vtable nadřazené třídy a lze ji použít pouze v rámci stejného sestavení, protože je interní.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="cd3ab-151">Přístupnost pro přepsání je však určena klíčovým slovem **Virtual** a může být přepsána z jiného sestavení, pokud má kód přístup ke třídě samotné.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="cd3ab-152">Pokud možnost přepsání představuje problém, použijte k opravě deklarativní zabezpečení nebo odeberte klíčové slovo **Virtual** , pokud není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="cd3ab-153">I v případě, že kompilátor jazyka zabraňuje těmto přepsáním s chybou kompilace, je možné kód napsaný s ostatními kompilátory přepsat.</span><span class="sxs-lookup"><span data-stu-id="cd3ab-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3ab-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd3ab-154">See also</span></span>

- [<span data-ttu-id="cd3ab-155">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="cd3ab-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
