---
title: Transparentní kód zabezpečení, úroveň 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 980c684bced685a61ad82ff5713ccff2b974028f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181132"
---
# <a name="security-transparent-code-level-1"></a>Transparentní kód zabezpečení, úroveň 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Transparentnost pomáhá vývojářům psát bezpečnější knihovny rozhraní .NET Framework, které zveřejňují funkce částečně důvěryhodnému kódu. Transparentnost úrovně 1 byla zavedena v rozhraní .NET Framework verze 2.0 a byla primárně používána pouze v rámci společnosti Microsoft. Počínaje rozhraním .NET Framework 4 můžete použít [průhlednost úrovně 2](security-transparent-code-level-2.md). Transparentnost úrovně 1 však byla zachována, takže můžete identifikovat starší kód, který musí být spuštěn s dřívějšími pravidly zabezpečení.  
  
> [!IMPORTANT]
> Měli byste zadat průhlednost úrovně 1 pouze pro kompatibilitu; to znamená, že zadejte úroveň 1 pouze pro kód, který byl vyvinut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> s rozhraním .NET Framework 3.5 nebo starší, který používá nebo nepoužívá model transparentnosti. Například použijte úroveň 1 průhlednosti pro sestavení rozhraní .NET Framework 2.0, které umožňují volání z částečně důvěryhodných volajících (APTCA). Pro kód, který je vyvinut pro rozhraní .NET Framework 4, vždy použijte transparentnost úrovně 2.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Model transparentnosti úrovně 1](#the_level_1_transparency_model)  
  
- [Atributy průhlednosti](#transparency_attributes)  
  
- [Příklady transparentnosti zabezpečení](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a>Model transparentnosti úrovně 1  
 Při použití transparentnosti úrovně 1 používáte model zabezpečení, který odděluje kód na transparentní, bezpečné a kritické pro zabezpečení a kritické pro zabezpečení.  
  
 Můžete označit celé sestavení, některé třídy v sestavení nebo některé metody ve třídě jako transparentní zabezpečení. Transparentní kód zabezpečení nemůže zvýšit oprávnění. Toto omezení má tři důsledky:  
  
- Transparentní kód zabezpečení <xref:System.Security.Permissions.SecurityAction.Assert> nemůže provádět akce.  
  
- Jakýkoli požadavek na propojení, který by byl uspokojen transparentním kódem zabezpečení, se stane úplným požadavkem.  
  
- Jakýkoli nebezpečný (neověřitelný) kód, který musí být spuštěn v kódu <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> transparentním pro zabezpečení, způsobí úplný požadavek na oprávnění zabezpečení.  
  
 Tato pravidla jsou vynucena během provádění za běhu společného jazyka (CLR). Transparentní kód zabezpečení předá všechny požadavky na zabezpečení kódu, který volá zpět svým volajícím. Požadavky, které toku prostřednictvím transparentní kód zabezpečení nelze zvýšit oprávnění. Pokud aplikace s nízkou důvěryhodností volá transparentní kód zabezpečení a způsobí požadavek na vysoké oprávnění, poptávka poteče zpět do kódu s nízkou důvěryhodností a selže. Transparentní kód zabezpečení nemůže zastavit poptávku, protože nemůže provádět akce assert. Stejný transparentní kód zabezpečení volaný z plně důvěryhodného kódu má za následek úspěšný požadavek.  
  
 Kritické pro zabezpečení je opakem transparentní ho zabezpečení. Kód kritický pro zabezpečení se provádí s úplným vztahem důvěryhodnosti a může provádět všechny privilegované operace. Bezpečný a kritický kód zabezpečení je privilegovaný kód, který prošel rozsáhlým auditem zabezpečení, aby se potvrdilo, že neumožňuje částečně důvěryhodným volajícím používat prostředky, ke kterým nemají oprávnění k přístupu.  
  
 Transparentnost musíte použít explicitně. Většina kódu, který zpracovává manipulaci s daty a logiku lze obvykle označit jako transparentní zabezpečení, zatímco menší množství kódu, který provádí zvýšení oprávnění je označen jako kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.  
  
> [!IMPORTANT]
> Transparentnost úrovně 1 je omezena na rozsah sestavení; není vynuceno mezi sestaveními. Transparentnost úrovně 1 byla primárně používána v rámci společnosti Microsoft pro účely auditu zabezpečení. Typy a členy kritické pro zabezpečení v rámci sestavení úrovně 1 lze přistupovat pomocí kódu transparentního zabezpečení v jiných sestaveních. Je důležité, abyste provedli požadavky na propojení pro úplnou důvěryhodnost ve všech typech a členech kritickém pro zabezpečení úrovně 1. Bezpečné zabezpečení a typy a členy musí také potvrdit, že volající mají oprávnění pro chráněné prostředky, které jsou přístupné typu nebo člena.  
  
 Pro zpětnou kompatibilitu s dřívějšími verzemi rozhraní .NET Framework jsou všichni členové, kteří nejsou anotováni s atributy průhlednosti, považováni za důležité pro zabezpečení a zabezpečení. Všechny typy, které nejsou anotovány, jsou považovány za průhledné. Neexistují žádná pravidla statické analýzy k ověření průhlednosti. Proto může být nutné ladit chyby průhlednosti za běhu.  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a>Atributy průhlednosti  
 Následující tabulka popisuje tři atributy, které používáte k oslnění kódu průhlednosti.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Povoleno pouze na úrovni sestavy. Identifikuje všechny typy a členy v sestavení jako transparentní pro zabezpečení. Sestavení nemůže obsahovat žádný kód kritický pro zabezpečení.|  
|<xref:System.Security.SecurityCriticalAttribute>|Při použití na úrovni <xref:System.Security.SecurityCriticalAttribute.Scope%2A> sestavení bez vlastnosti identifikuje veškerý kód v sestavení jako transparentní zabezpečení ve výchozím nastavení, ale označuje, že sestavení může obsahovat kód kritický pro zabezpečení.<br /><br /> Při použití na úrovni třídy identifikuje třídu nebo metodu jako kritické pro zabezpečení, ale ne členy třídy. Chcete-li, aby všechny členy <xref:System.Security.SecurityCriticalAttribute.Scope%2A> kritické <xref:System.Security.SecurityCriticalScope.Everything>pro zabezpečení, nastavte vlastnost na .<br /><br /> Při použití na úrovni člena se atribut vztahuje pouze na tohoto člena.<br /><br /> Třída nebo člen označený jako kritický pro zabezpečení může provádět zvýšení oprávnění. **Důležité:**  V transparentnosti úrovně 1 jsou typy a členy kritické pro zabezpečení považovány za kritické pro bezpečné zabezpečení, pokud jsou volány mimo sestavení. Měli byste chránit typy a členy kritické pro zabezpečení s požadavkem na propojení pro úplnou důvěryhodnost, abyste se vyhnuli neoprávněnému zvýšení oprávnění.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifikuje kód kritický pro zabezpečení, ke kterému lze přistupovat pomocí kódu transparentního pro zabezpečení v sestavení. V opačném případě kód transparentní zabezpečení nemůže přistupovat k soukromým nebo interním členům kritickým pro zabezpečení ve stejném sestavení. To by ovlivnilo kód kritický pro zabezpečení a umožnilo by to neočekávané zvýšení oprávnění. Bezpečný a kritický kód zabezpečení by měl projít přísným auditem zabezpečení. **Poznámka:**  Bezpečné zabezpečení a typy a členové musí ověřit oprávnění volajících k určení, zda má volající oprávnění k přístupu k chráněným prostředkům.|  
  
 Atribut <xref:System.Security.SecuritySafeCriticalAttribute> umožňuje transparentní kód zabezpečení pro přístup k členům kritickým pro zabezpečení ve stejném sestavení. Zvažte transparentní a kritický kód zabezpečení v sestavení jako rozdělený do dvou sestavení. Transparentní kód zabezpečení by nemohl zobrazit soukromé nebo interní členy kódu kritického pro zabezpečení. Kromě toho je kód kritický pro zabezpečení obecně auditován pro přístup k jeho veřejnému rozhraní. Neočekáváte, že soukromý nebo vnitřní stav bude přístupný mimo sestavení; byste chtěli zachovat stav izolovaný. Atribut <xref:System.Security.SecuritySafeCriticalAttribute> udržuje izolaci stavu mezi transparentní zabezpečení a kritické pro zabezpečení kódu a zároveň poskytuje možnost přepsat izolaci, když je to nezbytné. Transparentní kód zabezpečení nemůže přistupovat k soukromému nebo internímu <xref:System.Security.SecuritySafeCriticalAttribute>kódu důležitému pro zabezpečení, pokud tyto členy nebyly označeny . Před použitím <xref:System.Security.SecuritySafeCriticalAttribute>, audit tohoto člena, jako by byly veřejně vystaveny.  
  
### <a name="assembly-wide-annotation"></a>Anotace pro celou sestavu  
 Následující tabulka popisuje účinky použití atributů zabezpečení na úrovni sestavení.  
  
|Atribut sestavení|Stav sestavení|  
|------------------------|--------------------|  
|Žádný atribut v částečně důvěryhodném sestavení|Všechny typy a členy jsou transparentní.|  
|Žádný atribut v plně důvěryhodném sestavení (v globální mezipaměti `AppDomain`sestavení nebo identifikovaný jako úplný vztah důvěryhodnosti v )|Všechny typy jsou transparentní a všechny členy jsou důležité pro zabezpečení.|  
|`SecurityTransparent`|Všechny typy a členy jsou transparentní.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Všechny typy a členy jsou kritické pro zabezpečení.|  
|`SecurityCritical`|Všechny kód výchozí transparentní. Jednotlivé typy a členové však mohou mít jiné atributy.|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a>Příklady transparentnosti zabezpečení  
 Chcete-li použít pravidla průhlednosti rozhraní .NET Framework 2.0 (průhlednost úrovně 1), použijte následující poznámku sestavy:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Pokud chcete, aby celé sestavení transparentní označující, že sestavení neobsahuje žádný kritický kód a nezvyšuje oprávnění v žádném případě, můžete explicitně přidat průhlednost sestavení s následujícím atributem:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Pokud chcete kombinovat kritický a transparentní kód ve stejném sestavení, <xref:System.Security.SecurityCriticalAttribute> začněte označením sestavení atributem označující, že sestavení může obsahovat kritický kód, a to následovně:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Pokud chcete provádět akce kritické pro zabezpečení, musíte explicitně označit kód, <xref:System.Security.SecurityCriticalAttribute> který provede kritickou akci, jiným atributem, jak je znázorněno v následujícím příkladu kódu:  
  
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
  
 Předchozí kód je transparentní `Critical` s výjimkou metody, která je explicitně označena jako kritická pro zabezpečení. Průhlednost je výchozí nastavení, a <xref:System.Security.SecurityCriticalAttribute> to i s atributem na úrovni sestavení.  
  
## <a name="see-also"></a>Viz také

- [Transparentní kód pro zabezpečení, úroveň 2](security-transparent-code-level-2.md)
- [Změny zabezpečení](../security/security-changes.md)
