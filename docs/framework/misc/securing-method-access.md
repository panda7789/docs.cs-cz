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
# <a name="securing-method-access"></a>Zabezpečení přístupu k metodě
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Některé metody nemusí být vhodné pro povolení volání libovolného nedůvěryhodného kódu. Tyto metody představují několik rizik: Metoda může poskytnout některé omezené informace; mohlo by věřit, že jí byly předány jakékoli informace; nemusí provést kontrolu chyb na parametrech; nebo se špatnými parametry, může dojít k poruše nebo dělat něco škodlivého. Měli byste si být vědomi těchto případů a přijmout opatření k ochraně metody.  
  
 V některých případech může být nutné omezit metody, které nejsou určeny pro veřejné použití, ale stále musí být veřejné. Můžete mít například rozhraní, které musí být voláno napříč vlastními knihovnami DLL, a proto musí být veřejné, ale nechcete jej veřejně vystavit, abyste zabránili zákazníkům v jeho používání nebo aby škodlivý kód nemohl zneužívat vstupní bod do komponenty. Dalším běžným důvodem k omezení metody, která není určena pro veřejné použití (ale musí být veřejná), je vyhnout se nutnosti dokumentovat a podporovat to, co může být velmi interní rozhraní.  
  
 Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodám:  
  
- Omezte rozsah usnadnění pro třídu, sestavení nebo odvozené třídy, pokud mohou být důvěryhodné. Toto je nejjednodušší způsob, jak omezit přístup k metodě. Všimněte si, že obecně odvozené třídy může být méně důvěryhodné než třídy, které jsou odvozeny z, i když v některých případech sdílejí identitu nadřazené třídy. Zejména neodvodit důvěru z **klíčového**slova chráněné , který není nutně použit v kontextu zabezpečení.  
  
- Omezte přístup metody volajícím zadané identity – v podstatě všechny konkrétní [důkazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (silný název, vydavatel, zóna a tak dále), které zvolíte.  
  
- Omezte přístup metody k volajícím, kteří mají jakákoli oprávnění, která vyberete.  
  
 Podobně deklarativní zabezpečení umožňuje řídit dědičnost tříd. Můžete použít **InheritanceDemand** provést následující:  
  
- Vyžadovat odvozené třídy mít zadanou identitu nebo oprávnění.  
  
- Vyžadovat odvozené třídy, které přepíší určité metody, aby měly zadanou identitu nebo oprávnění.  
  
 Následující příklad ukazuje, jak pomoci chránit veřejnou třídu pro omezený přístup tím, že vyžaduje, aby volající být podepsány s určitým silným názvem. Tento příklad <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> používá s **Demand pro** silný název. Informace o tom, jak podepsat sestavení se silným názvem, naleznete v tématu [Vytváření a používání sestavení se silným názvem](../../standard/assembly/create-use-strong-named.md).  
  
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
 Pomocí deklarací uvedených v této části můžete zabránit použití určitých tříd a metod, vlastností a událostí částečně důvěryhodným kódem. Použitím těchto deklarací na třídu použijete ochranu na všechny její metody, vlastnosti a události; upozorňujeme však, že přístup k polím není deklarativním zabezpečením ovlivněn. Všimněte si také, že požadavky na propojení pomáhají chránit pouze před bezprostředními volajícími a mohou být stále předmětem lákavých útoků.  
  
> [!NOTE]
> Nový model transparentnosti byl zaveden v rozhraní .NET Framework 4. [Transparentní kód zabezpečení,](security-transparent-code-level-2.md) model úrovně 2 identifikuje <xref:System.Security.SecurityCriticalAttribute> zabezpečený kód s atributem. Kód kritický pro zabezpečení vyžaduje, aby volající i dědicové byli plně důvěryhodní. Sestavení spuštěná pod pravidly zabezpečení přístupu kódu z dřívějších verzí rozhraní .NET Framework mohou volat sestavení úrovně 2. V takovém případě budou atributy kritické pro zabezpečení považovány za požadavky na propojení pro úplnou důvěryhodnost.  
  
 V sestaveních se silným názvem [linkdemand](link-demands.md) je použita pro všechny veřejně přístupné metody, vlastnosti a události v něm omezit jejich použití plně důvěryhodných volajících. Chcete-li tuto funkci zakázat, je nutné použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Proto explicitně označení třídy vyloučit nedůvěryhodné volající je nezbytné pouze pro nepodepsané sestavení nebo sestavení s tímto atributem; tyto deklarace můžete označit podmnožinu typů v něm, které nejsou určeny pro nedůvěryhodné volající.  
  
 Následující příklady ukazují, jak zabránit tomu, aby třídy a členové používali nedůvěryhodný kód.  
  
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
  
 Pro veřejné přepsat funkce, kde základní třída nevyžaduje úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejné přepsat funkce, kde základní třída vyžaduje plnou důvěryhodnost:  
  
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
> Tato část varuje o problému se zabezpečením `virtual` `internal` při`Overloads` `Overridable` `Friend` deklarování metody jako oba a ( v jazyce Visual Basic). Toto upozornění platí pouze pro rozhraní .NET Framework verze 1.0 a 1.1, nevztahuje se na novější verze.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1, musíte být vědomi nuance přístupnosti systému typu při potvrzování, že váš kód není k dispozici pro jiná sestavení. Metoda, která je deklarována **virtuální** a **interní** **(Přetížení overridable Friend** v jazyce Visual Basic) může přepsat položku vtable nadřazené třídy a lze ji použít pouze ze stejného sestavení, protože je interní. Přístupnost pro přepsání je však určena **virtuální** klíčové slovo a to může být přepsána z jiného sestavení tak dlouho, dokud tento kód má přístup k samotné třídy. Pokud možnost přepsání představuje problém, použijte deklarativní zabezpečení opravit nebo odebrat **virtuální** klíčové slovo, pokud není nezbytně nutné.  
  
 Všimněte si, že i v případě, že kompilátor jazyka brání tyto přepsání s chybou kompilace, je možné pro kód napsaný s jinými kompilátory přepsat.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
