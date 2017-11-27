---
title: "Kód transparentní pro zabezpečení, úroveň 1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
caps.latest.revision: "32"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bdc1a4f9afb8b1d7cf56b74a329353100accc46d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code-level-1"></a>Kód transparentní pro zabezpečení, úroveň 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Transparentnost pomáhá vývojářům psát bezpečnější knihovny rozhraní .NET Framework, které poskytují funkcionalitu částečně důvěryhodným kódem. Průhlednost úrovně 1 byla zavedena v rozhraní .NET Framework verze 2.0 a byla primárně používá pouze v rámci Microsoftu. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít [průhlednost úrovně 2](../../../docs/framework/misc/security-transparent-code-level-2.md). Průhlednost úrovně 1 však byly ponechány, takže můžete identifikovat starší kód, který musí být spuštěna s starší pravidla zabezpečení.  
  
> [!IMPORTANT]
>  Musíte zadat průhlednost úrovně 1 pouze pro kompatibilitu; To znamená, zadejte úroveň 1 pouze pro kód, který byla vyvinuta v rozhraní .NET Framework 3.5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> nebo nepoužívá model transparentnosti. Průhlednost úrovně 1 můžete například použijte pro sestavení rozhraní .NET Framework 2.0, které umožňují volání z částečně důvěryhodné volající (APTCA). Pro kód, který je vyvinutý pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vždy použijte průhlednost úrovně 2.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Model průhlednost úrovně 1](#the_level_1_transparency_model)  
  
-   [Atributy průhlednosti](#transparency_attributes)  
  
-   [Příklady transparentnosti zabezpečení](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Model průhlednost úrovně 1  
 Pokud použijete průhlednost úrovně 1, používáte model zabezpečení, který odděluje kód do metody transparentní pro zabezpečení, bezpečné a kritické pro zabezpečení a kritické pro zabezpečení.  
  
 Můžete označit celé sestavení, některé třídy v sestavení nebo některé metody v třídě jako transparentní pro zabezpečení. Kód transparentní pro zabezpečení nelze zvýšit oprávnění. Toto omezení má tři důsledky:  
  
-   Kód transparentní pro zabezpečení nelze provést <xref:System.Security.Permissions.SecurityAction.Assert> akce.  
  
-   Každý požadavek na propojení, které by vyhovět kód transparentní pro zabezpečení se změní na úplný požadavek.  
  
-   Jakýkoliv nebezpečný (neověřitelný) kód, který musí být spuštěn v kód transparentní pro zabezpečení způsobuje úplný požadavek pro <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění zabezpečení.  
  
 Tato pravidla se vynucují během provádění modulem common language runtime (CLR). Kód transparentní pro zabezpečení předává všechny požadavky na zabezpečení kód, který volá zpět jeho volající. Vyžaduje, aby tok prostřednictvím kód transparentní pro zabezpečení nelze zvýšit oprávnění. Pokud málo důvěryhodná aplikace volá kód transparentní pro zabezpečení a způsobí, že žádost o vysoká oprávnění, vyžádání tok nízká důvěryhodný kód, který se nezdaří. Kód transparentní pro zabezpečení nemůže žádost zastavit, protože nelze provést assert akce. Stejný kód transparentní pro zabezpečení volat z kódu plné důvěryhodnosti výsledky v úspěšnou žádost.  
  
 Kritický pro zabezpečení je opakem transparentní pro zabezpečení. Kód kritický pro zabezpečení provede s úplným vztahem důvěryhodnosti a může provádět všechny privilegovaného operace. Bezpečné a kritické pro zabezpečení kód je privilegovaný kód, který byl prostřednictvím rozsáhlého auditu zabezpečení potvrďte, že neumožňuje částečně důvěryhodné volající využívat prostředky, které nemají oprávnění k přístupu.  
  
 Budete muset použít průhlednost explicitně. Většina vašeho kódu, která zpracovává manipulaci s daty a logiku může být obvykle označený jako transparentní pro zabezpečení, zatímco menší množství kód, který provádí zvýšení oprávnění je označena jako kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.  
  
> [!IMPORTANT]
>  Průhlednost úrovně 1 je omezen na rozsah sestavení; není vynucena mezi sestavení. Průhlednost úrovně 1 se primárně v rámci společnosti Microsoft pro účely auditu zabezpečení. Typy kritické pro zabezpečení a členy v rámci sestavení úroveň 1 je přístupný kód transparentní pro zabezpečení v jiné sestavení. Je důležité provést požadavky propojení pro úplný vztah důvěryhodnosti v typy kritické pro zabezpečení na úrovni 1 a členy. Bezpečné a kritické pro zabezpečení typy a členy musí také ověřit, že volající mají oprávnění pro chráněné prostředky, které jsou dostupné přes typ nebo člen.  
  
 Pro zpětnou kompatibilitu s předchozími verzemi služby rozhraní .NET Framework všechny členy, kteří nejsou poznámky transparentnosti atributy jsou považovány za bezpečné a kritické pro zabezpečení. Všechny typy, které nejsou poznámky jsou považovány za transparentní. Neexistují žádná pravidla statické analýzy ověření průhlednost. Potřebujete tedy ladění průhlednost chyby za běhu.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atributy průhlednosti  
 Následující tabulka popisuje tři atributy, které použijete k přidání poznámek ke kódu pro průhlednost.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Povoleny pouze na úrovni sestavení. Identifikuje všechny typy a členy v sestavení jako transparentní pro zabezpečení. Sestavení nesmí obsahovat žádné kód kritický pro zabezpečení.|  
|<xref:System.Security.SecurityCriticalAttribute>|Při použití na úrovni sestavení bez <xref:System.Security.SecurityCriticalAttribute.Scope%2A> vlastnost identifikuje všechny kód v sestavení jako transparentní pro zabezpečení ve výchozím nastavení, ale označuje, že sestavení může obsahovat kód kritický pro zabezpečení.<br /><br /> Při použití na úrovni třídy, identifikuje třída nebo metoda jako kritické pro zabezpečení, ale ne členy třídy. Aby všichni členové kritické pro zabezpečení, nastavte <xref:System.Security.SecurityCriticalAttribute.Scope%2A> vlastnost <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Pokud se použije na úrovni člena, atribut se vztahuje pouze na tohoto člena.<br /><br /> Třída nebo člen označený jako kritické pro zabezpečení můžete provádět zvyšování oprávnění. **Důležité:** v průhlednost úrovně 1, typy a členy kritické pro zabezpečení zacházeno jako bezpečné a kritické pro zabezpečení při jsou volány z mimo sestavení. Měli byste chránit typy kritické pro zabezpečení a členy s požadavek propojení pro úplný vztah důvěryhodnosti, aby se zabránilo neoprávněnému zvýšení úrovně oprávnění.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Určuje kód kritický pro zabezpečení, který je přístupný kód transparentní pro zabezpečení v sestavení. Kód transparentní pro zabezpečení, jinak hodnota nemůže přistupovat k privátní nebo interní kritické pro zabezpečení členům ve stejném sestavení. Díky tomu by ovlivnit kód kritický pro zabezpečení a umožňují neočekávané zvýšení oprávnění. Bezpečné a kritické pro zabezpečení kód by měl projít přísným auditem zabezpečení. **Poznámka:** bezpečné a kritické pro zabezpečení typy a členy musíte ověřit oprávnění volajícím určit, zda má volající oprávnění pro přístup k chráněným prostředkům.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Atribut umožňuje kód transparentní pro zabezpečení pro přístup k kritické pro zabezpečení členů ve stejném sestavení. Kód transparentní pro zabezpečení a kritické pro zabezpečení ve vaší sestavení zvažte, jak je rozdělené do dvou sestavení. Kód transparentní pro zabezpečení se budou moci zobrazit členy soukromý nebo interní kód kritický pro zabezpečení. Kromě toho kód kritický pro zabezpečení je obecně auditovaný pro přístup k jeho veřejné rozhraní. Nebude očekávat stavu soukromý nebo interní byly přístupné mimo sestavení; by chcete zachovat stav izolované. <xref:System.Security.SecuritySafeCriticalAttribute> Atribut udržuje izolaci stavu mezi kód transparentní pro zabezpečení a kritické pro zabezpečení zároveň poskytuje možnost přepsat izolaci, když je to nutné. Kód transparentní pro zabezpečení nelze přistupovat k privátní nebo interní kód kritický pro zabezpečení, pokud bylo označeno těmto členům s <xref:System.Security.SecuritySafeCriticalAttribute>. Před použitím <xref:System.Security.SecuritySafeCriticalAttribute>, jako kdyby byl veřejně vystaven audit tohoto člena.  
  
### <a name="assembly-wide-annotation"></a>Sestavení celou poznámky  
 Následující tabulka popisuje účinky pomocí atributů zabezpečení na úrovni sestavení.  
  
|Atribut sestavení|Stav sestavení|  
|------------------------|--------------------|  
|Žádný atribut v částečně důvěryhodné sestavení|Všechny typy a členy jsou transparentní.|  
|Žádný atribut v plně důvěryhodný pro sestavení (v globální mezipaměti sestavení nebo identifikován jako úplný vztah důvěryhodnosti v `AppDomain`)|Všechny typy jsou transparentní a bezpečné a kritické pro zabezpečení se všichni její členové.|  
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Všechny typy a členy jsou kritické pro zabezpečení.|  
|`SecurityCritical`|Všechny kódu automaticky transparentní. Jednotlivé typy a členy však mohou mít jiné atributy.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Příklady transparentnosti zabezpečení  
 Pokud chcete používat pravidla transparentnosti rozhraní .NET Framework 2.0 (úroveň 1 průhlednost), použijte následující anotaci sestavení:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Pokud chcete, aby celé sestavení transparentní znamenat, že sestavení neobsahuje žádný kritický kód a nezvyšuje oprávnění žádným způsobem, můžete přidat průhlednost explicitně do sestavení s následující atribut:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Pokud chcete kombinovat kritický a transparentní kód ve stejném sestavení, spusťte toto sestavení s označením <xref:System.Security.SecurityCriticalAttribute> atribut k označení, že sestavení může obsahovat kód kritický pro následujícím způsobem:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Pokud chcete provést akce kritické pro zabezpečení, je třeba explicitně označit kód, který provede kritické akce pomocí jiného <xref:System.Security.SecurityCriticalAttribute> atributu, jak je znázorněno v následujícím příkladu kódu:  
  
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
  
 Předchozí kód je transparentní s výjimkou `Critical` metoda, která je explicitně označena jako kritické pro zabezpečení. Průhlednost je výchozí nastavení, i když úrovně sestavení <xref:System.Security.SecurityCriticalAttribute> atribut.  
  
## <a name="see-also"></a>Viz také  
 [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)  
 [Změny zabezpečení](../../../docs/framework/security/security-changes.md)
