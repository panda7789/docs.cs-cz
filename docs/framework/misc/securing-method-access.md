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
ms.openlocfilehash: d4b2bab09d9ac9f14ae9d1bf78254c9c6a376677
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691473"
---
# <a name="securing-method-access"></a>Zabezpečení přístupu k metodě
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Některé metody nemusí být vhodný umožňující libovolného nedůvěryhodný kód pro volání. Tyto metody představují několik rizika: Metoda může poskytnout určité omezené informace; může věřit žádné informace o předán. nemusí provést kontrolu chyb na parametry. nebo se nesprávné parametry, může selhat nebo škodlivé něco udělat. By měl mít na paměti tyto případy a provedete akce vedoucí k ochraně metodu.  
  
 V některých případech můžete potřebovat k omezení metody, které nejsou určeny pro veřejně přístupný, ale přesto musejí být veřejné. Například může být rozhraní, které musí být volána v rámci vlastní knihovny DLL a proto musí být veřejné, ale nechcete zveřejnit veřejně, aby se zabránilo zákazníci využívat nebo zabránit škodlivým kódem využívajícím vstupní bod do příslušné součásti. Dalším běžným důvodem k omezení metody nejsou určené pro veřejně přístupný (ale musí být veřejná) je vyhnout se nutnosti dokumentů a podpory, které mohou být velmi interní rozhraní.  
  
 Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodě:  
  
-   Omezte její obor usnadnění přístupu pro třídy, sestavení nebo odvozené třídy, pokud se může považovat za důvěryhodné. Toto je nejjednodušší způsob, jak omezit přístup k metodě. Všimněte si, že obecně odvozené třídy mohou být méně důvěryhodné než třídy, které vyplývají z, i když v některých případech sdílejí identity nadřazené třídy. Zejména nelze odvodit vztah důvěryhodnosti z klíčového slova **chráněné**, což není nutně použít v kontextu zabezpečení.  
  
-   Omezit přístup k metodě volajícím zadané identity – v podstatě žádné konkrétní [důkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatele, zóny a podobně) vyberete.  
  
-   Omezte přístup metoda volajícím mají všechna oprávnění, které jste vybrali.  
  
 Deklarativní zabezpečení obdobně umožňuje řídit dědičnosti tříd. Můžete použít **InheritanceDemand** můžete provádět následující:  
  
-   Vyžadovat odvozené třídy zadané identity nebo oprávnění.  
  
-   Vyžadovat odvozené třídy, které přepíší specifických metod mít zadané identity nebo oprávnění.  
  
 Následující příklad ukazuje, jak můžete ochránit veřejnou třídu pro omezený přístup tím, že vyžaduje, aby byly podepsány volající konkrétní silným názvem. V tomto příkladu <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> s **vyžádání** pro silný název. Založený na úlohách informace o tom, jak podepsat sestavení silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>Vyloučení tříd a členů z použití nedůvěryhodným kódem  
 Jak zabránit používán částečně důvěryhodným kódem konkrétní třídy a metody, stejně jako vlastnosti a události, pomocí deklarace uvedené v této části. Použitím tyto deklarace třídy nastavují ochranu pro všechny jeho metody, vlastnosti a události. Mějte však na paměti, že přístup k poli není ovlivněn deklarativní zabezpečení. Všimněte si také, že požadavky propojení pomáhá chránit před jenom okamžitý volající a můžou i nadále být vystavené útokům typu luring.  
  
> [!NOTE]
>  Nový model transparentnosti je zavedený v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) identifikuje zabezpečený kód pomocí modelu <xref:System.Security.SecurityCriticalAttribute> atribut. Kód kritický pro zabezpečení vyžaduje volající a dědice plně důvěryhodné. Sestavení, které jsou spuštěny v pravidla zabezpečení přístupu kódu z předchozích verzí rozhraní .NET Framework mohou volat sestavení úrovně 2. Kritické pro zabezpečení atributy v tomto případě bude zacházeno jako požadavky propojení pro úplný vztah důvěryhodnosti.  
  
 V sestavení se silným názvem [LinkDemand](../../../docs/framework/misc/link-demands.md) platí pro všechny veřejně přístupné metody, vlastnosti a události v něm můžete omezit jejich použití k plně důvěryhodné volající. Pokud chcete zakázat tuto funkci, musíte použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Proto explicitní označení třídy pro vyloučení nedůvěryhodných volajících je potřebný jenom u nepodepsaná sestavení nebo sestavení pomocí tohoto atributu. můžete použít tyto deklarace k označení podmnožinu typů v něm, které nejsou určeny pro nedůvěryhodných volajících.  
  
 Následující příklady ukazují, jak zabránit používá nedůvěryhodný kód třídy a členy.  
  
 Pro veřejné neuzavřené třídy:  
  
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
  
 Pro veřejné zapečetěné třídy:  
  
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
  
 Pro veřejné abstraktní třídy:  
  
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
  
 Pro veřejnou virtuální funkce:  
  
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
  
 Pro veřejné abstraktní funkce:  
  
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
  
 Pro veřejné funkce přepsání Pokud základní třída nevyžaduje úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejné funkce přepsání kde základní třídy vyžaduje úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejné rozhraní:  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Virtuální interní přepisy nebo přetížení přepsatelného přítele  
  
> [!NOTE]
>  V této části upozorní potíže se zabezpečením při deklaraci metody jako `virtual` a `internal` (`Overloads``Overridable``Friend` v jazyce Visual Basic). Toto upozornění se vztahuje pouze na rozhraní .NET Framework verze 1.0 a 1.1, nevztahuje se na novější verze.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1 musíte být vědomi nuance typ – usnadnění systému při potvrzení, že váš kód je k dispozici pro jiná sestavení. Metoda, která je deklarována **virtuální** a **interní** (**přetížení přepsatelného přítele** v jazyce Visual Basic) můžete přepsat položku vtable nadřazené třídy a lze použít pouze v v rámci stejného sestavení vzhledem k tomu, že je interní. Ale je určená pro usnadnění pro přepsání **virtuální** – klíčové slovo a to může být přepsána z jiného sestavení za předpokladu, že kód má přístup k samotné třídě. Pokud možnost přepsat představuje problém, používejte deklarativní zabezpečení a opravit ho nebo odebrat **virtuální** – klíčové slovo, pokud to není nezbytně nutné.  
  
 Všimněte si, že i v případě, že kompilátor jazyka zabraňuje tato přepsání kvůli chybě kompilace, je možné pro kód zapisovaný s jinými kompilátory pro přepsání.  
  
## <a name="see-also"></a>Viz také:
- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
