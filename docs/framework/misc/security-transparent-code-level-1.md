---
title: Kód transparentní pro zabezpečení, úroveň 1
description: Seznamte se s příklady transparentnosti úrovně 1, atributy transparentnosti a transparentnost zabezpečení.
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: c44fe3339f3bf24d266fa97487868ce090d51bb1
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309091"
---
# <a name="security-transparent-code-level-1"></a>Kód transparentní pro zabezpečení, úroveň 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Transparentnost pomáhá vývojářům psát bezpečnější .NET Framework knihovny, které zpřístupňují funkce částečně důvěryhodnému kódu. Transparentnost první úrovně byla představena v .NET Framework verze 2,0 a byla primárně používána pouze v rámci společnosti Microsoft. Počínaje .NET Framework 4 můžete použít [transparentnost úrovně 2](security-transparent-code-level-2.md). Transparentnost první úrovně ale byla zachovaná, takže můžete identifikovat starší kód, který musí běžet s předchozími pravidly zabezpečení.  
  
> [!IMPORTANT]
> Měli byste zadat transparentnost první úrovně pouze pro kompatibilitu; To znamená, že zadejte úroveň 1 pouze pro kód vyvinutý s .NET Framework 3,5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nebo nepoužívá model transparentnosti. Například použijte transparentnost první úrovně pro sestavení .NET Framework 2,0, která umožňují volání z částečně důvěryhodných volajících (APTCA). Pro kód vyvinutý pro .NET Framework 4 vždy použijte transparentnost úrovně 2.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Model transparentnosti úrovně 1](#the_level_1_transparency_model)  
  
- [Atributy transparentnosti](#transparency_attributes)  
  
- [Příklady transparentnosti zabezpečení](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a>Model transparentnosti úrovně 1  
 Pokud používáte transparentnost první úrovně, používáte model zabezpečení, který odděluje kód do bezpečnostních a transparentních metod, které jsou bezpečné pro zabezpečení a kritické pro zabezpečení.  
  
 Můžete označit celé sestavení, některé třídy v sestavení nebo některé metody ve třídě jako transparentní pro zabezpečení. Kód transparentní pro zabezpečení nemůže zvýšit oprávnění. Toto omezení má tři důsledky:  
  
- Kód transparentní pro zabezpečení nemůže provádět <xref:System.Security.Permissions.SecurityAction.Assert> akce.  
  
- Všechny požadavky propojení, které by byly splněny kódem transparentním z bezpečnostních potřeb, se stávají úplnými požadavky.  
  
- Jakýkoli nezabezpečený (neověřitelný) kód, který musí být spuštěn v kódu transparentním z bezpečnostních důvodů, způsobuje plný požadavek na <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění zabezpečení.  
  
 Tato pravidla jsou vynutila během provádění modulem CLR (Common Language Runtime). Kód transparentní pro zabezpečení předává všechny požadavky na zabezpečení kódu, který volá zpět na jeho volající. Požadavky, které tok prostřednictvím kódu transparentního z důvodu zabezpečení nemohou zvýšit oprávnění. Pokud aplikace s nízkou důvěryhodností volá kód transparentní pro zabezpečení a způsobuje poptávku s vysokým oprávněním, požadavek se přesměruje zpět na kód s nízkou důvěryhodností a selže. Kód transparentní z důvodu zabezpečení nemůže zastavit požadavek, protože nemůže provádět kontrolní akce. Stejný transparentní kód, který je volán z plně důvěryhodného kódu, má za následek úspěšnou poptávku.  
  
 Kritické zabezpečení je opakem transparentního z hlediska zabezpečení. Kód kritický pro zabezpečení se spouští s úplným vztahem důvěryhodnosti a může provádět všechny privilegované operace. Bezpečný a kritický kód je privilegovaný kód, který byl prostřednictvím rozsáhlého auditu zabezpečení, aby bylo možné ověřit, že neumožňuje částečně důvěryhodným volajícím používat prostředky, ke kterým nemají oprávnění k přístupu.  
  
 Transparentnost je nutné použít explicitně. Většina vašeho kódu, který zpracovává manipulaci s daty a logiku, může být obvykle označena jako transparentní z hlediska zabezpečení, zatímco menší množství kódu, který provádí zvýšení oprávnění, je označeno jako kritické pro zabezpečení nebo bezpečné pro zabezpečení.  
  
> [!IMPORTANT]
> Transparentnost první úrovně je omezená na rozsah sestavení; není vynutilo mezi sestaveními. Transparentnost první úrovně se primárně používala v rámci Microsoftu pro účely auditu zabezpečení. Typy a členy kritické pro zabezpečení v rámci sestavení úrovně 1 mohou být k dispozici v kódu transparentním z hlediska zabezpečení v jiných sestaveních. Je důležité, abyste provedli požadavky propojení na úplný vztah důvěryhodnosti ve všech typech a členech, které jsou kritické pro zabezpečení úrovně 1. Typy a členy kritické pro zabezpečení musí také potvrdit, že volající mají oprávnění k chráněným prostředkům, ke kterým má přístup daný typ nebo člen.  
  
 Pro zpětnou kompatibilitu s předchozími verzemi .NET Framework jsou všichni členové, kteří nejsou poopatřeni atributy transparentnosti, považováni za bezpečné a kritické pro zabezpečení. Všechny typy, které nejsou opatřeny poznámkami, jsou považovány za transparentní. Nejsou k dispozici žádná pravidla statických analýz pro ověření transparentnosti. Proto může být nutné ladit chyby transparentnosti v době běhu.  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a>Atributy transparentnosti  
 V následující tabulce jsou popsány tři atributy, které lze použít k přidání poznámky k vašemu kódu k průhlednosti.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Povoluje se jenom na úrovni sestavení. Identifikuje všechny typy a členy v sestavení jako transparentní z hlediska zabezpečení. Sestavení nemůže obsahovat žádný kód kritický pro zabezpečení.|  
|<xref:System.Security.SecurityCriticalAttribute>|Při použití na úrovni sestavení bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> Vlastnosti identifikuje všechny kódy v sestavení jako zabezpečení transparentní ve výchozím nastavení, ale označuje, že sestavení může obsahovat kód kritický pro zabezpečení.<br /><br /> Při použití na úrovni třídy identifikuje třídu nebo metodu jako kritické pro zabezpečení, ale ne členy třídy. Pro zajištění kritického zabezpečení všech členů nastavte <xref:System.Security.SecurityCriticalAttribute.Scope%2A> vlastnost na hodnotu <xref:System.Security.SecurityCriticalScope.Everything> .<br /><br /> Při použití na úrovni člena platí atribut pouze pro daného člena.<br /><br /> Třída nebo člen identifikovaný jako kritické pro zabezpečení mohou provádět zvýšení oprávnění. **Důležité informace:**  V transparentnosti úrovně 1 jsou typy a členy kritické pro zabezpečení považovány za bezpečné – kritické, pokud jsou volány mimo sestavení. Je nutné chránit typy a členy kritické pro zabezpečení s požadavkem na propojení pro úplný vztah důvěryhodnosti, aby se předešlo neoprávněnému zvýšení oprávnění.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifikuje kód kritický pro zabezpečení, ke kterému lze přistupovat pomocí transparentního kódu v sestavení. V opačném případě kód transparentní z hlediska zabezpečení nemůže přistupovat ke soukromým nebo interním členům kritickým pro zabezpečení ve stejném sestavení. Tím by došlo k ovlivnění kódu kritického pro zabezpečení a zajištění neočekávaných zvýšení oprávnění. Bezpečný a kritický kód pro zabezpečení by měl projít přísným auditem zabezpečení. **Poznámka:**  Typy a členy kritické pro zabezpečení musí ověřit oprávnění volajících a určit, zda má volající oprávnění k přístupu k chráněným prostředkům.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute>Atribut umožňuje kódu transparentnímu z hlediska zabezpečení přistupovat ke členům kritickým pro zabezpečení ve stejném sestavení. Ve vašem sestavení zvažte kód transparentní z hlediska zabezpečení a kritický pro zabezpečení, který je rozdělen do dvou sestavení. Kód transparentní z hlediska zabezpečení by nedokázal zobrazit soukromé nebo interní členy kódu kritického pro zabezpečení. Kód kritický pro zabezpečení je kromě toho obecně auditován pro přístup k jeho veřejnému rozhraní. Neočekáváte, že privátní nebo interní stav bude přístupný mimo sestavení; Chcete zachovat stav izolované. <xref:System.Security.SecuritySafeCriticalAttribute>Atribut udržuje izolaci stavu mezi kódem transparentním z hlediska zabezpečení a kritickým pro zabezpečení a zároveň nabízí možnost přepsat izolaci, pokud je to nezbytné. Kód transparentní z hlediska zabezpečení nemůže získat přístup k privátnímu nebo internímu kódu kritickému pro zabezpečení, pokud tyto členy nebyly označeny <xref:System.Security.SecuritySafeCriticalAttribute> . Před použitím <xref:System.Security.SecuritySafeCriticalAttribute> proveďte audit tohoto člena, jako kdyby byl veřejně vystavený.  
  
### <a name="assembly-wide-annotation"></a>Poznámka na úrovni sestavení  
 Následující tabulka popisuje účinky použití atributů zabezpečení na úrovni sestavení.  
  
|Atribut Assembly|Stav sestavení|  
|------------------------|--------------------|  
|Žádný atribut v částečně důvěryhodném sestavení|Všechny typy a členy jsou transparentní.|  
|Žádný atribut v plně důvěryhodném sestavení (v globální mezipaměti sestavení (GAC) nebo identifikovaný jako úplný vztah důvěryhodnosti v rozhraní `AppDomain` )|Všechny typy jsou transparentní a všechny členy jsou bezpečné a kritické pro zabezpečení.|  
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Všechny typy a členy jsou kritické pro zabezpečení.|  
|`SecurityCritical`|Veškerý kód je standardně transparentní. Jednotlivé typy a členy však mohou mít jiné atributy.|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a>Příklady transparentnosti zabezpečení  
 Chcete-li použít pravidla transparentnosti .NET Framework 2,0 (transparentnost první úrovně), použijte následující anotaci sestavení:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Pokud chcete, aby celé sestavení bylo transparentní pro indikaci, že sestavení neobsahuje žádný kritický kód a nezvyšuje oprávnění jakýmkoli způsobem, můžete explicitně přidat průhlednost do sestavení s následujícím atributem:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Pokud chcete ve stejném sestavení kombinovat klíč kritického a transparentního kódu, začněte tím, že označíte sestavení s <xref:System.Security.SecurityCriticalAttribute> atributem k označení toho, že sestavení může obsahovat kritický kód, a to takto:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Chcete-li provést akce kritické pro zabezpečení, je nutné explicitně označit kód, který provede kritickou akci s jiným <xref:System.Security.SecurityCriticalAttribute> atributem, jak je znázorněno v následujícím příkladu kódu:  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 Předchozí kód je transparentní s výjimkou `Critical` metody, která je explicitně označena jako kritická pro zabezpečení. Transparentnost je výchozí nastavení, dokonce i s atributem na úrovni sestavení <xref:System.Security.SecurityCriticalAttribute> .  
  
## <a name="see-also"></a>Viz také

- [Transparentní kód pro zabezpečení, úroveň 2](security-transparent-code-level-2.md)
- [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
