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
ms.openlocfilehash: 5d083af6abc91121ebbc9554d03c635cabe2bbd9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217130"
---
# <a name="securing-method-access"></a>Zabezpečení přístupu k metodě
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Některé metody nemusí být vhodné, aby bylo možné volat libovolný nedůvěryhodný kód. Tyto metody představují několik rizik: metoda může poskytovat nějaké omezené informace; může se stát, že se budou předávat nějaké informace; nemusí provádět kontrolu chyb u parametrů; nebo s chybnými parametry může být nefunkční nebo něco škodlivého. Měli byste si být vědomi těchto případů a provést akci, která vám pomůžou ochránit tuto metodu.  
  
 V některých případech možná budete muset omezit metody, které nejsou určené pro veřejné použití, ale pořád musí být veřejné. Například můžete mít rozhraní, které je třeba volat napříč vašimi vlastními knihovnami DLL, a proto musí být veřejné, ale nechcete zveřejnit ho veřejně, aby se zabránilo zákazníkům v jeho použití, nebo aby se zabránilo škodlivému kódu v zneužití vstupního bodu do vaší komponenty. Dalším běžným důvodem pro omezení metody, která není určená pro veřejné použití (ale musí být veřejná), je vyhnout se nutnosti dokumentovat a podporovat to, co by mohlo být velmi interní rozhraní.  
  
 Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodě:  
  
- Omezte rozsah dostupnosti pro třídu, sestavení nebo odvozené třídy, pokud mohou být důvěryhodné. Toto je nejjednodušší způsob, jak omezit přístup k metodě. Všimněte si, že obecně odvozené třídy mohou být méně důvěryhodné než třída odvozená z, i když v některých případech sdílí identitu nadřazené třídy. Konkrétně neodvozujte důvěryhodnost z **chráněného**klíčového slova, které se nutně nepoužívá v kontextu zabezpečení.  
  
- Omezte přístup k metodě u volajících zadané identity – v podstatě všechny konkrétní [legitimace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatel, zóna atd.) si můžete vybrat.  
  
- Omezte přístup k metodě volajících, která mají jakákoli oprávnění, která jste vybrali.  
  
 Podobně deklarativní zabezpečení umožňuje řídit dědičnost tříd. **InheritanceDemand** můžete použít k následujícím akcím:  
  
- Vyžaduje, aby odvozené třídy měly zadanou identitu nebo oprávnění.  
  
- Vyžadovat odvozené třídy, které přepíší konkrétní metody, aby měly zadanou identitu nebo oprávnění.  
  
 Následující příklad ukazuje, jak přispět k ochraně veřejné třídy pro omezený přístup tím, že vyžaduje, aby volající byli podepsáni pomocí konkrétního silného názvu. V tomto příkladu se používá <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> s **poptávkou** pro silný název. Informace o tom, jak podepsat sestavení se silným názvem, naleznete v tématu [vytváření a používání sestavení se silným názvem](../../standard/assembly/create-use-strong-named.md).  
  
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
 Použijte deklarace uvedené v této části, chcete-li zabránit konkrétním třídám a metodám, a také k vlastnostem a událostem, od použití částečně důvěryhodným kódem. Použitím těchto deklarací u třídy můžete použít ochranu na všechny metody, vlastnosti a události. Upozorňujeme však, že přístup k poli není ovlivněn deklarativním zabezpečením. Všimněte si také, že požadavky na propojení můžou chránit jenom před okamžitými volajícími a můžou se i nadále luring útoky.  
  
> [!NOTE]
> Nový model transparentnosti se zavedl do .NET Framework 4. [Kód transparentní z hlediska zabezpečení, model úrovně 2,](security-transparent-code-level-2.md) identifikuje zabezpečený kód s atributem <xref:System.Security.SecurityCriticalAttribute>. Kód kritický pro zabezpečení vyžaduje, aby volající a dědice byly plně důvěryhodné. Sestavení, která jsou spuštěna pod pravidly zabezpečení přístupu kódu z dřívějších .NET Framework verzí, mohou volat sestavení úrovně 2. V takovém případě budou atributy kritické pro zabezpečení považovány za požadavky propojení pro úplný vztah důvěryhodnosti.  
  
 V sestavení se silným názvem je [LinkDemand](link-demands.md) použit pro všechny veřejně přístupné metody, vlastnosti a události v rámci omezení jejich použití pro plně důvěryhodné volající. Chcete-li tuto funkci zakázat, je nutné použít atribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Proto explicitní označení tříd pro vyloučení nedůvěryhodných volajících je nezbytné pouze pro nepodepsaná sestavení nebo sestavení s tímto atributem; Tyto deklarace lze použít k označení podmnožiny typů, které nejsou určeny pro nedůvěryhodné volající.  
  
 Následující příklady ukazují, jak zabránit používání tříd a členů pomocí nedůvěryhodného kódu.  
  
 Pro veřejné nezapečetěné třídy:  
  
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
  
 Pro veřejné virtuální funkce:  
  
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
  
 Pro veřejné funkce přepsání, kde základní třída nesplňuje požadavky na úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejné funkce přepsání, kde základní třída požaduje úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejná rozhraní:  
  
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
> Tato část upozorňuje na problémy zabezpečení při deklaraci metody jako `virtual` i `internal` (`Overloads` `Overridable` `Friend` v Visual Basic). Toto upozornění se vztahuje pouze na verze .NET Framework 1,0 a 1,1, ale nevztahuje se na novější verze.  
  
 V .NET Framework verzích 1,0 a 1,1 je nutné znát nuance typu přístupnost systému při potvrzení, že váš kód není k dispozici jiným sestavením. Metoda, která je deklarována jako **Virtual** a **interní** (přepisovatelných**přátel** v Visual Basic) může přepsat položku vtable nadřazené třídy a lze ji použít pouze v rámci stejného sestavení, protože je interní. Přístupnost pro přepsání je však určena klíčovým slovem **Virtual** a může být přepsána z jiného sestavení, pokud má kód přístup ke třídě samotné. Pokud možnost přepsání představuje problém, použijte k opravě deklarativní zabezpečení nebo odeberte klíčové slovo **Virtual** , pokud není nezbytně nutné.  
  
 Všimněte si, že i v případě, že kompilátor jazyka zabrání těmto přepsáním s chybou kompilace, je možné kód napsaný s jinými kompilátory přepsat.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
