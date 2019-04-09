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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2159199fc12ef83a6bf4a44841d71799e0dad4dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166176"
---
# <a name="securing-method-access"></a><span data-ttu-id="11308-102">Zabezpečení přístupu k metodě</span><span class="sxs-lookup"><span data-stu-id="11308-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="11308-103">Některé metody nemusí být vhodný umožňující libovolného nedůvěryhodný kód pro volání.</span><span class="sxs-lookup"><span data-stu-id="11308-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="11308-104">Tyto metody představují několik rizika: Metoda může poskytnout určité omezené informace; může věřit žádné informace o předán. nemusí provést kontrolu chyb na parametry. nebo se nesprávné parametry, může selhat nebo škodlivé něco udělat.</span><span class="sxs-lookup"><span data-stu-id="11308-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="11308-105">By měl mít na paměti tyto případy a provedete akce vedoucí k ochraně metodu.</span><span class="sxs-lookup"><span data-stu-id="11308-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="11308-106">V některých případech můžete potřebovat k omezení metody, které nejsou určeny pro veřejně přístupný, ale přesto musejí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="11308-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="11308-107">Například může být rozhraní, které musí být volána v rámci vlastní knihovny DLL a proto musí být veřejné, ale nechcete zveřejnit veřejně, aby se zabránilo zákazníci využívat nebo zabránit škodlivým kódem využívajícím vstupní bod do příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="11308-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="11308-108">Dalším běžným důvodem k omezení metody nejsou určené pro veřejně přístupný (ale musí být veřejná) je vyhnout se nutnosti dokumentů a podpory, které mohou být velmi interní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11308-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="11308-109">Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodě:</span><span class="sxs-lookup"><span data-stu-id="11308-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="11308-110">Omezte její obor usnadnění přístupu pro třídy, sestavení nebo odvozené třídy, pokud se může považovat za důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="11308-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="11308-111">Toto je nejjednodušší způsob, jak omezit přístup k metodě.</span><span class="sxs-lookup"><span data-stu-id="11308-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="11308-112">Všimněte si, že obecně odvozené třídy mohou být méně důvěryhodné než třídy, které vyplývají z, i když v některých případech sdílejí identity nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="11308-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="11308-113">Zejména nelze odvodit vztah důvěryhodnosti z klíčového slova **chráněné**, což není nutně použít v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11308-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="11308-114">Omezit přístup k metodě volajícím zadané identity – v podstatě žádné konkrétní [důkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatele, zóny a podobně) vyberete.</span><span class="sxs-lookup"><span data-stu-id="11308-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="11308-115">Omezte přístup metoda volajícím mají všechna oprávnění, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="11308-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="11308-116">Deklarativní zabezpečení obdobně umožňuje řídit dědičnosti tříd.</span><span class="sxs-lookup"><span data-stu-id="11308-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="11308-117">Můžete použít **InheritanceDemand** můžete provádět následující:</span><span class="sxs-lookup"><span data-stu-id="11308-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="11308-118">Vyžadovat odvozené třídy zadané identity nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="11308-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="11308-119">Vyžadovat odvozené třídy, které přepíší specifických metod mít zadané identity nebo oprávnění.</span><span class="sxs-lookup"><span data-stu-id="11308-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="11308-120">Následující příklad ukazuje, jak můžete ochránit veřejnou třídu pro omezený přístup tím, že vyžaduje, aby byly podepsány volající konkrétní silným názvem.</span><span class="sxs-lookup"><span data-stu-id="11308-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="11308-121">V tomto příkladu <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> s **vyžádání** pro silný název.</span><span class="sxs-lookup"><span data-stu-id="11308-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="11308-122">Založený na úlohách informace o tom, jak podepsat sestavení silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="11308-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="11308-123">Vyloučení tříd a členů z použití nedůvěryhodným kódem</span><span class="sxs-lookup"><span data-stu-id="11308-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="11308-124">Jak zabránit používán částečně důvěryhodným kódem konkrétní třídy a metody, stejně jako vlastnosti a události, pomocí deklarace uvedené v této části.</span><span class="sxs-lookup"><span data-stu-id="11308-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="11308-125">Použitím tyto deklarace třídy nastavují ochranu pro všechny jeho metody, vlastnosti a události. Mějte však na paměti, že přístup k poli není ovlivněn deklarativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11308-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="11308-126">Všimněte si také, že požadavky propojení pomáhá chránit před jenom okamžitý volající a můžou i nadále být vystavené útokům typu luring.</span><span class="sxs-lookup"><span data-stu-id="11308-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11308-127">Nový model transparentnosti je zavedený v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11308-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="11308-128">[Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) identifikuje zabezpečený kód pomocí modelu <xref:System.Security.SecurityCriticalAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="11308-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="11308-129">Kód kritický pro zabezpečení vyžaduje volající a dědice plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="11308-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="11308-130">Sestavení, které jsou spuštěny v pravidla zabezpečení přístupu kódu z předchozích verzí rozhraní .NET Framework mohou volat sestavení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="11308-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="11308-131">Kritické pro zabezpečení atributy v tomto případě bude zacházeno jako požadavky propojení pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="11308-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="11308-132">V sestavení se silným názvem [LinkDemand](../../../docs/framework/misc/link-demands.md) platí pro všechny veřejně přístupné metody, vlastnosti a události v něm můžete omezit jejich použití k plně důvěryhodné volající.</span><span class="sxs-lookup"><span data-stu-id="11308-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="11308-133">Pokud chcete zakázat tuto funkci, musíte použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="11308-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="11308-134">Proto explicitní označení třídy pro vyloučení nedůvěryhodných volajících je potřebný jenom u nepodepsaná sestavení nebo sestavení pomocí tohoto atributu. můžete použít tyto deklarace k označení podmnožinu typů v něm, které nejsou určeny pro nedůvěryhodných volajících.</span><span class="sxs-lookup"><span data-stu-id="11308-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="11308-135">Následující příklady ukazují, jak zabránit používá nedůvěryhodný kód třídy a členy.</span><span class="sxs-lookup"><span data-stu-id="11308-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="11308-136">Pro veřejné neuzavřené třídy:</span><span class="sxs-lookup"><span data-stu-id="11308-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="11308-137">Pro veřejné zapečetěné třídy:</span><span class="sxs-lookup"><span data-stu-id="11308-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="11308-138">Pro veřejné abstraktní třídy:</span><span class="sxs-lookup"><span data-stu-id="11308-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="11308-139">Pro veřejnou virtuální funkce:</span><span class="sxs-lookup"><span data-stu-id="11308-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="11308-140">Pro veřejné abstraktní funkce:</span><span class="sxs-lookup"><span data-stu-id="11308-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="11308-141">Pro veřejné funkce přepsání Pokud základní třída nevyžaduje úplný vztah důvěryhodnosti:</span><span class="sxs-lookup"><span data-stu-id="11308-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="11308-142">Pro veřejné funkce přepsání kde základní třídy vyžaduje úplný vztah důvěryhodnosti:</span><span class="sxs-lookup"><span data-stu-id="11308-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="11308-143">Pro veřejné rozhraní:</span><span class="sxs-lookup"><span data-stu-id="11308-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="11308-144">Virtuální interní přepisy nebo přetížení přepsatelného přítele</span><span class="sxs-lookup"><span data-stu-id="11308-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11308-145">V této části upozorní potíže se zabezpečením při deklaraci metody jako `virtual` a `internal` (`Overloads` `Overridable` `Friend` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="11308-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="11308-146">Toto upozornění se vztahuje pouze na rozhraní .NET Framework verze 1.0 a 1.1, nevztahuje se na novější verze.</span><span class="sxs-lookup"><span data-stu-id="11308-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="11308-147">V rozhraní .NET Framework verze 1.0 a 1.1 musíte být vědomi nuance typ – usnadnění systému při potvrzení, že váš kód je k dispozici pro jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="11308-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="11308-148">Metoda, která je deklarována **virtuální** a **interní** (**přetížení přepsatelného přítele** v jazyce Visual Basic) můžete přepsat položku vtable nadřazené třídy a lze použít pouze v v rámci stejného sestavení vzhledem k tomu, že je interní.</span><span class="sxs-lookup"><span data-stu-id="11308-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="11308-149">Ale je určená pro usnadnění pro přepsání **virtuální** – klíčové slovo a to může být přepsána z jiného sestavení za předpokladu, že kód má přístup k samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="11308-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="11308-150">Pokud možnost přepsat představuje problém, používejte deklarativní zabezpečení a opravit ho nebo odebrat **virtuální** – klíčové slovo, pokud to není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="11308-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="11308-151">Všimněte si, že i v případě, že kompilátor jazyka zabraňuje tato přepsání kvůli chybě kompilace, je možné pro kód zapisovaný s jinými kompilátory pro přepsání.</span><span class="sxs-lookup"><span data-stu-id="11308-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11308-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11308-152">See also</span></span>

- [<span data-ttu-id="11308-153">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="11308-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
