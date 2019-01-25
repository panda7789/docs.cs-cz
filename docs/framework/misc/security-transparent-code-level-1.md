---
title: Kód transparentní pro zabezpečení, úroveň 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 485579df9c3976d70d2560c10d74f0402f48492e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590386"
---
# <a name="security-transparent-code-level-1"></a>Kód transparentní pro zabezpečení, úroveň 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Průhlednost pomáhá vývojářům psát bezpečnější knihovny rozhraní .NET Framework, které poskytují funkce, které částečně důvěryhodným kódem. Transparentnosti úrovně 1 byla zavedena v rozhraní .NET Framework verze 2.0 a byla primárně používána pouze v rámci Microsoftu. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít [transparentnosti úrovně 2](../../../docs/framework/misc/security-transparent-code-level-2.md). Ale transparentnosti úrovně 1 byly ponechány, aby mohli identifikovat starší kód, který musí být spuštěn s starší pravidla zabezpečení.  
  
> [!IMPORTANT]
>  Je třeba zadat transparentnosti úrovně 1 pouze pro kompatibilitu; To znamená, specifikovat úroveň 1 pouze pro kód, který byl vyvinut v rozhraní .NET Framework 3.5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nebo nepoužívá model transparentnosti. Například použijte transparentnosti úrovně 1 pro sestavení rozhraní .NET Framework 2.0, které umožňují volání od částečně důvěryhodných volajících (APTCA). Pro kód, který je vyvinutý pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vždy použijte transparentnost druhé úrovně 2.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Model transparentnosti úrovně 1](#the_level_1_transparency_model)  
  
-   [Atributy transparentnosti](#transparency_attributes)  
  
-   [Příklady transparentnosti zabezpečení](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Model transparentnosti úrovně 1  
 Pokud používáte transparentnosti úrovně 1, použijete model zabezpečení, který odděluje kód do metody transparentní pro zabezpečení, bezpečné a kritické pro zabezpečení a kritické pro zabezpečení.  
  
 Můžete označit celé sestavení, některé třídy v sestavení nebo některé metody v třídě jako transparentní pro zabezpečení. Kód transparentní pro zabezpečení nelze zvýšit oprávnění. Toto omezení má tři důsledky:  
  
-   Bezpečnostně transparentní kód nemůže provádět <xref:System.Security.Permissions.SecurityAction.Assert> akce.  
  
-   Každý požadavek na propojení, které budou splněna díky zabezpečení transparentního kódu se změní na úplný požadavek.  
  
-   Unsafe (neověřitelný) kód, který musí být spuštěn v kód transparentní pro zabezpečení způsobí, že úplný poptávka <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění zabezpečení.  
  
 Tato pravidla vynucují během provádění modulem common language runtime (CLR). Kód transparentní pro zabezpečení předává všechny požadavky na zabezpečení kódu, který volá zpět do jeho volající. Vyžaduje, aby tok prostřednictvím kód transparentní pro zabezpečení nelze zvýšit oprávnění. Pokud nízká důvěryhodnosti aplikace volá kód transparentní pro zabezpečení a způsobí, že poptávka vysoká oprávnění, vyžádání tok s nízkou důvěryhodného kódu, který se nezdaří. Kód transparentní pro zabezpečení nelze zastavit vyžádání, protože nelze provést kontrolní výraz akce. Stejný kód transparentní pro zabezpečení volat z plně důvěryhodného kódu výsledky úspěšného poptávky.  
  
 Kritické z hlediska zabezpečení je opakem transparentní pro zabezpečení. Kód kritický pro zabezpečení se spustí s úplným vztahem důvěryhodnosti a mohou provádět všechny privilegované operace. Bezpečné a kritické pro zabezpečení kódu je privileged kód, který prošel rozsáhlého auditu zabezpečení potvrďte, že neumožňuje volání částečně důvěryhodným volajícím použít prostředky nemají oprávnění k přístupu.  
  
 Je nutné explicitní použití průhlednosti. Většinu kódu, která zpracovává manipulaci s daty a logiky může být označený jako transparentní pro zabezpečení, obvykle, že menší množství kódu, který provádí zvýšení oprávnění je označen jako kritické pro zabezpečení nebo bezpečný a kritický pro zabezpečení.  
  
> [!IMPORTANT]
>  Je omezený na obor sestavení; transparentnosti úrovně 1 nevynucuje se mezi sestaveními. Transparentnosti úrovně 1 byla primárně používána v rámci společnosti Microsoft pro účely auditu zabezpečení. Typy kritické pro zabezpečení a členy v rámci sestavení úrovni 1 je přístupný kód transparentní pro zabezpečení v jiných sestaveních. Je důležité, abyste provedli požadavky propojení pro všechny typy kritické pro zabezpečení úrovně 1 a členové úplný vztah důvěryhodnosti. Bezpečné a kritické pro zabezpečení typů a členů musí také ověřit, že volající nemá oprávnění pro chráněné prostředky, které jsou dostupné přes tento typ nebo člen.  
  
 Z důvodu zpětné kompatibility s předchozími verzemi rozhraní .NET Framework všechny členy, které nejsou označena s atributy transparentnosti jsou považovány za bezpečné a kritické pro zabezpečení. Všechny typy, které nejsou s poznámkami, jsou považovány za průhledné. Nejsou žádná pravidla statické analýzy pro ověření transparentnosti. Proto budete muset ladit chyby transparentnosti v době běhu.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atributy transparentnosti  
 Následující tabulka popisuje tři atributy, které použijete k přidání poznámek ke kódu transparentnosti.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Povoleno pouze na úrovni sestavení. Identifikuje všechny typy a členy v sestavení jako transparentní pro zabezpečení. Sestavení nemůže obsahovat žádný kód kritický pro zabezpečení.|  
|<xref:System.Security.SecurityCriticalAttribute>|Pokud se použije na úrovni sestavení bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> vlastnost, identifikuje všechny kódu v sestavení jako transparentní pro zabezpečení ve výchozím nastavení, ale indikuje, že sestavení může obsahovat kritický kód pro zabezpečení.<br /><br /> Když se použije na úrovni třídy, určuje třída nebo metoda jako kritické pro zabezpečení, ale ne členy třídy. Chcete-li všechny členy kritické z hlediska zabezpečení, nastavte <xref:System.Security.SecurityCriticalAttribute.Scope%2A> vlastnost <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Když se použije na úrovni člena, atribut platí jenom pro tohoto člena.<br /><br /> Třída nebo člen identifikovány jako kritické pro zabezpečení můžete provádět zvyšování oprávnění. **Důležité:**  V transparentnosti úrovně 1 typy a členy kritické pro zabezpečení se bude zacházet jako bezpečné a kritické pro zabezpečení když jsou volaní mimo sestavení. By měla chránit kritické pro zabezpečení typů a členů pomocí požadavku propojení pro úplný vztah důvěryhodnosti, aby neoprávněné zvýšení úrovně oprávnění.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifikuje kritické pro zabezpečení kód, který je přístupný kód transparentní pro zabezpečení v sestavení. V opačném případě bezpečnostně transparentní kód nemůže přistupovat k privátní nebo interní kritické pro zabezpečení členům ve stejném sestavení. Mohlo by ovlivnit kód kritický pro zabezpečení a umožňují neočekávané zvýšení oprávnění. Zabezpečení – bezpečný a kritický kód by měl být podroben striktní bezpečnostní auditu. **Poznámka:**  Bezpečné a kritické pro zabezpečení typů a členů musí ověřit oprávnění volajících k určení, zda volající nemá oprávnění pro přístup k chráněným prostředkům.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Atribut umožňuje kód transparentní pro zabezpečení pro přístup ke členům kritické pro zabezpečení ve stejném sestavení. Kód transparentní pro zabezpečení a kritické pro zabezpečení v sestavení zvažte, jak rozdělené na dvě sestavení. Kód transparentní pro zabezpečení nebude moct zobrazit soukromé nebo interní členy kód kritický pro zabezpečení. Kromě toho kód kritický pro zabezpečení se Audituje obecně pro přístup k jeho veřejné rozhraní. Očekáváte by privátní nebo interní stav bude přístupná mimo sestavení; Chcete zachovat stav izolované. <xref:System.Security.SecuritySafeCriticalAttribute> Atribut zajišťuje izolaci stavu mezi kód transparentní pro zabezpečení a kritické pro zabezpečení v případě potřeby přepsat izolaci současně. Kód transparentní pro zabezpečení nelze přistupovat k privátní nebo interní zabezpečení kritického kódu, pokud tyto členy jsou označené pomocí <xref:System.Security.SecuritySafeCriticalAttribute>. Před použitím <xref:System.Security.SecuritySafeCriticalAttribute>, audit, se kterou, jako kdyby byly veřejně zpřístupnit.  
  
### <a name="assembly-wide-annotation"></a>Celé sestavení poznámky  
 Následující tabulka popisuje důsledky používání atributy zabezpečení na úrovni sestavení.  
  
|Atribut sestavení|Stav sestavení|  
|------------------------|--------------------|  
|Žádný atribut pro částečně důvěryhodná sestavení|Všechny typy a členy jsou transparentní.|  
|Žádný atribut pro plně důvěryhodná sestavení (v globální mezipaměti sestavení nebo označen jako úplný vztah důvěryhodnosti v `AppDomain`)|Všechny typy jsou transparentní a bezpečné a kritické pro zabezpečení jsou všichni členové.|  
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Všechny typy a členy jsou kritické pro zabezpečení.|  
|`SecurityCritical`|Všechny výchozí hodnoty pro transparentní kód. Nicméně jednotlivé typy a členy mohou mít jiné atributy.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Příklady transparentnosti zabezpečení  
 Pokud chcete použít pravidla transparentnosti rozhraní .NET Framework 2.0 (transparentnosti úrovně 1), použijte následující poznámka sestavení:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Pokud chcete na průhledný celé sestavení k označení, že sestavení neobsahuje žádné kritického kódu a není zvýšení oprávnění v žádným způsobem, můžete explicitně přidat průhlednost na sestavení s následující atribut:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Pokud chcete kombinovat kritické a transparentní kód ve stejném sestavení, začněte tím, že označení sestavení <xref:System.Security.SecurityCriticalAttribute> atribut označuje, že sestavení může obsahovat kritický kód, následujícím způsobem:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Pokud chcete provést akce kritické pro zabezpečení, je třeba explicitně označit kód, který bude provádět důležité akci s jinou <xref:System.Security.SecurityCriticalAttribute> atributu, jak je znázorněno v následujícím příkladu kódu:  
  
```  
[assembly: SecurityCritical]  
Public class A  
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
  
 Předchozí kód je transparentní, s výjimkou `Critical` metoda, která je explicitně označena jako kritické pro zabezpečení. Transparentnost je ve výchozím nastavení je i při úrovni sestavení <xref:System.Security.SecurityCriticalAttribute> atribut.  
  
## <a name="see-also"></a>Viz také:
- [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
- [Změny zabezpečení](../../../docs/framework/security/security-changes.md)
