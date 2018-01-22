---
title: "Zabezpečení přístupu k metodě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf894239db623b34d23757edd1c39d3652a7e0f7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="securing-method-access"></a>Zabezpečení přístupu k metodě
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Některé metody nemusí být vhodné pro povolení libovolného nedůvěryhodného kódu k volání. Tyto metody představují několik rizika: metoda může poskytovat některé informace s omezeným přístupem; může věřit všechny informace do ní; nemusí provést kontrolu chyb na parametry; nebo se nesprávné parametry, může selhat nebo udělat něco škodlivého. Musí mít na paměti tyto případy a provést akci k ochraně metodu.  
  
 V některých případech může být nutné k omezení metody, které nejsou určeny pro veřejné použití, ale stále musí být veřejné. Například může mít rozhraní, které musí být voláno prostřednictvím vlastních knihoven DLL a proto musí být veřejné, ale nechcete zveřejnění veřejně zákazníkům zabránit použití nebo zabránit zneužití vstupním bodem do příslušné součásti škodlivý kód. Jiné běžným důvodem k omezení metody není určen pro veřejné (ale musí být veřejná) je-li se vyhnout dokumentů a podpory, které mohou být velmi vnitřní rozhraní.  
  
 Spravovaný kód nabízí několik způsobů, jak omezit přístup k metodě:  
  
-   Omezte rozsah usnadnění přístupu ke třídě, sestavení nebo odvozené třídy, pokud mohou být důvěryhodné. Toto je nejjednodušší způsob, jak omezit přístup k metodě. Všimněte si, že obecně odvozených tříd může být méně důvěryhodné než třídy, na kterou odvozují, i když v některých případech sdílejí identity nadřazené třídy. Konkrétně nelze odvodit důvěryhodnosti z klíčového slova **chráněné**, který není nutně používá v kontextu zabezpečení.  
  
-   Omezit přístup k metodě pro volající zadané identity--v podstatě žádné konkrétní [důkaz](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (silný název, vydavatele, zóně a tak dále) zvolíte.  
  
-   Omezte přístup metoda pro volající mají všechna oprávnění, které vyberete.  
  
 Podobně deklarativní zabezpečení umožňuje řízení dědění tříd. Můžete použít **InheritanceDemand** proveďte následující:  
  
-   Odvozené třídy mít zadanou identitou nebo oprávnění vyžadují.  
  
-   Odvozené třídy, které potlačí konkrétní metody mít zadanou identitou nebo oprávnění vyžadují.  
  
 Následující příklad ukazuje, jak k ochraně veřejnou třídu pro omezený přístup vyžadováním, aby byly podepsány volající konkrétní silným názvem. Tento příklad používá <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> s **vyžádání** pro silný název. Založený na úlohách informace o tom, jak podepsání sestavení se silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Pomocí deklarace uvedené v této části zabránit, aby určité třídy a metody, a také vlastnosti a události, používal částečně důvěryhodným kódem. Použitím tyto deklarace na třídu použijete ochranu pro všechny její metody, vlastnosti a události; Všimněte si však, že přístup k poli není ovlivněn deklarativní zabezpečení. Všimněte si také, že požadavky na odkaz zajistit ochranu proti pouze okamžitou volající a může podléhat stále útokům typu luring.  
  
> [!NOTE]
>  Nový model průhlednost byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelu identifikuje zabezpečený kód pomocí <xref:System.Security.SecurityCriticalAttribute> atribut. Kód kritický pro zabezpečení vyžaduje volající a dědice být plně důvěryhodná. Sestavení, které jsou spuštěny v pravidla zabezpečení přístupu kódu z dřívějších verzí rozhraní .NET Framework můžete volat sestavení úrovně 2. V takovém případě kritické pro zabezpečení atributy budou považovány za požadavky na odkaz pro úplný vztah důvěryhodnosti.  
  
 V sestavení se silným názvem [LinkDemand](../../../docs/framework/misc/link-demands.md) se použije na všechny veřejně přístupné metody, vlastnosti a události v něm omezil jejich použití u plně důvěryhodný pro volající. Chcete-li tuto funkci zakázat, je nutné použít <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut. Proto explicitní označení tříd pro vyloučení nedůvěryhodných volajících je potřebný jenom u nepodepsaná sestavení nebo sestavení pomocí tohoto atributu; můžete použít tyto deklarace v něm označit podmnožinu typy, které nejsou určeny pro nedůvěryhodné volající.  
  
 Následující příklady ukazují, jak zabránit používá nedůvěryhodnými třídy a členy.  
  
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
  
 Pro veřejné uzavřené třídy:  
  
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
public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
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
abstract class Base2{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 Pro veřejné funkce přepsání kde základní třída nevyžaduje úplný vztah důvěryhodnosti:  
  
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
  
 Pro veřejné funkce přepsání kde základní třída vyžaduje úplný vztah důvěryhodnosti:  
  
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
>  V této části upozorní o porušení zabezpečení deklarace metody jako obou `virtual` a `internal` (`Overloads``Overridable``Friend` v jazyce Visual Basic). Toto upozornění se vztahuje pouze na rozhraní .NET Framework verze 1.0 a 1.1, nevztahuje se na novější verzi.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1 musíte být vědomi nuance usnadnění systému typ při potvrzení, že váš kód je k dispozici jiným sestavením. Metoda, která je deklarovaná **virtuální** a **interní** (**přetížení přepsatelné** v jazyce Visual Basic) můžete přepsat položku vtable nadřazené třídy a dá se použít jenom z v rámci stejného sestavení vzhledem k tomu, že je interní. Nicméně, je dáno usnadnění přístupu pro přepsání **virtuální** – klíčové slovo a to může být přepsáno z jiného sestavení, dokud tento kód má přístup k vlastní třídy. Pokud možnost přepsat vytváří problém, použijte deklarativní zabezpečení opravit nebo odebrat **virtuální** – klíčové slovo, pokud není nezbytně nutné.  
  
 Všimněte si, že i v případě, že kompilátor jazyka brání tato přepsání kvůli chybě kompilace, je možné pro kód zapisovaný s jinými kompilátory přepsat.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
