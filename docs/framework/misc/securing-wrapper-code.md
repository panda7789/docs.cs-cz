---
title: Zabezpečení kódu obálky
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4d8497d17e1a82791f4dd6ca8f91c9a012db167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132779"
---
# <a name="securing-wrapper-code"></a>Zabezpečení kódu obálky
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kód obálky, zejména pokud má obálka vyšší zabezpečení než kód, který používá, můžete otevřít jedinečnou sadu slabá místa zabezpečení. Všechno Hotovo jménem volající, kde omezenými oprávněními volajícího, jež nejsou součástí kontroly zabezpečení, je potenciální slabé stránky na možné zneužít.  
  
 Nikdy nepovolujte něco prostřednictvím obálky, kterou volajícího nelze provést samotný. Toto je speciální nebezpečí při děláte něco, co zahrnuje omezenou kontrolu zabezpečení, na rozdíl od úplné procházení zásobníku. Pokud se jedná o jednu úroveň kontroly obálkového kódu mezi skutečné volajícího a elementu rozhraní API v otázce může snadno způsobit kontrola zabezpečení uspět, když ji by měl není, čímž oslabí zabezpečení.  
  
## <a name="delegates"></a>Delegáty  
 Delegát zabezpečení se liší mezi verzemi rozhraní .NET Framework.  Tato část popisuje chování různých delegáta a související důležité informace o zabezpečení.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Ve verzi 1.0 a 1.1 rozhraní .NET Framework  
 Verze 1.0 a 1.1 rozhraní .NET Framework provést následující akce zabezpečení proti delegáta creator a volající delegáta.  
  
-   Po vytvoření delegáta požadavky na zabezpečení propojení na cílové metody delegáta jsou provedeny udělená sada oprávnění tvůrce delegáta.  Výsledkem nesplnění akce zabezpečení <xref:System.Security.SecurityException>.  
  
-   Když je vyvolán delegát, jsou prováděny existující požadavků na zabezpečení na volajícím delegáta.  
  
 Vždy, když má váš kód <xref:System.Delegate> z méně důvěryhodnému kódu, který může volat, ujistěte se, že nejsou povolení méně důvěryhodnému kódu ke zvýšení úrovně oprávnění. Je-li provést delegáta a pozdější použití, kód, který vytvoří delegát není v zásobníku volání a jeho oprávnění nebudou testována, pokud kód v nebo v rámci delegáta pokusí chráněné operace. Pokud váš kód a volající kód oprávnění vyšší než tvůrce, Tvůrce můžete orchestrovat cesta volání bez části zásobníku volání.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Ve verzi 2.0 a novějších verzích rozhraní .NET Framework  
 Na rozdíl od předchozích verzí verze 2.0 a novějších verzích rozhraní .NET Framework provede akce zabezpečení proti delegáta creator delegáta je vytvořen a volat.  
  
-   Po vytvoření delegáta požadavky na zabezpečení propojení na cílové metody delegáta jsou provedeny udělená sada oprávnění tvůrce delegáta.  Výsledkem nesplnění akce zabezpečení <xref:System.Security.SecurityException>.  
  
-   Udělená sada tvůrce příslušného delegáta je také zaznamenána během vytvoření delegáta a uložená s delegátem.  
  
-   Když je vyvolán delegát, Tvůrce příslušného delegáta zachycené udělené sady nejprve vyhodnocení proti všechny požadavky v rámci aktuálního kontextu, pokud delegáta creator a volající patří do různých sestaveních.  Dále jsou prováděny existující požadavků na zabezpečení na volajícím delegáta.  
  
## <a name="link-demands-and-wrappers"></a>Požadavky na propojení a obálky  
 Zvláštní případ ochrany s požadavky propojení má posílena v rámci infrastruktury zabezpečení, ale je stále zdrojem je možné slabé stránky ve vašem kódu.  
  
 Pokud plně důvěryhodného kódu volá vlastnosti, události nebo metody, které jsou chráněné službou [LinkDemand](../../../docs/framework/misc/link-demands.md), bude volání úspěšné, pokud **LinkDemand** kontrola oprávnění pro volající není splněna. Kromě toho pokud plně důvěryhodného kódu zpřístupní třídu, která přebírá název vlastnosti a volání jeho **získat** přístupového objektu pomocí reflexe, toto volání **získat** přistupujícího objektu bude úspěšné, i když nemá uživatelský kód není nutné oprávnění k přístupu k této vlastnosti. Je to proto, **LinkDemand** kontroluje pouze okamžitého volajícího, což je plně důvěryhodného kódu. V podstatě plně důvěryhodného kódu je volání privilegovaných jménem uživatelský kód bez a ujistěte se, že uživatelský kód má oprávnění provést toto volání.  
  
 Takové bezpečnostních děr zabránit, modul common language runtime rozšiřuje kontrolu do požadavek na úplné procházení zásobníku na všechny nepřímé volání metody, konstruktor, vlastnost nebo událost chráněn **LinkDemand**. Tato ochrana náklady na výkon s sebou nese náklady a změny sémantiky kontrola zabezpečení; vyžádání úplné procházení zásobníku může selhat, pokud by prošly rychlejší a jednu úroveň kontroly.  
  
## <a name="assembly-loading-wrappers"></a>Sestavení – načítání obálek  
 Několik metod používaných k načtení spravovaného kódu, včetně <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, načtení sestavení s legitimací volajícího. Pokud zabalením některé z těchto metod, pomocí zabezpečení systému udělení oprávnění kódu, namísto oprávnění volajícímu obálku, a načte tato sestavení. By nemělo umožňovat méně důvěryhodnému kódu načíst kód, který je vyšší oprávnění než u volajícího, aby vaše obálky.  
  
 Veškerý kód, který má úplný vztah důvěryhodnosti nebo výrazně vyšší zabezpečení než potenciální volající (včetně volajícího úroveň oprávnění Internetu), může oslabit zabezpečení tímto způsobem. Pokud váš kód má veřejnou metodu, která přijímá pole bajtů a předává jej do **Assembly.Load**, a tím vytváření sestavení jménem volajícího, by mohly narušit zabezpečení.  
  
 Tento problém se vztahuje k následujícím prvkům rozhraní API:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Vyžádání vs. LinkDemand  
 Deklarativní zabezpečení nabízí dva druhy kontroly zabezpečení, které jsou podobné, ale provést kontroly velmi odlišné. Protože nesprávné volby může způsobit ztrátu slabý výkon nebo zabezpečení, měli byste porozumět obě formy.  
  
 Deklarativní zabezpečení nabízí následující kontroly zabezpečení:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand> Určuje procházení zásobníku zabezpečení přístupu kódu. Zadané oprávnění nebo identity předat musí mít všichni volající v zásobníku. **Vyžádání** dochází při každém volání, protože zásobník může obsahovat různé volající. Pokud zavoláte metodu opakovaně, vyvolá tuto kontrolu zabezpečení pokaždé, když. **Vyžádání** je dobrá ochrana proti útokům typu luring; neoprávněný kód. při operaci get přes něj bude rozpoznán.  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md) dochází v době kompilace just-in-time (JIT) a kontroluje pouze bezprostředního volajícího. Tato kontrola zabezpečení volajícího, volající nekontroluje. Jakmile úspěšně proběhne kontrola, neexistuje žádné další bezpečnostní režie nezáleží na tom, kolikrát může volající volat. Existuje ale také žádná ochrana proti útokům typu luring. S **LinkDemand**, veškerý kód, který projde testem a může odkazovat na váš kód může potenciálně narušit zabezpečení tím, že škodlivý kód volání pomocí autorizovaného kódu. Proto nepoužívejte **LinkDemand** Pokud nebude možné slabá místa můžete důkladně vyhnout.  
  
    > [!NOTE]
    >  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly nahrazeny požadavky propojení <xref:System.Security.SecurityCriticalAttribute> atribut <xref:System.Security.SecurityRuleSet.Level2> sestavení. <xref:System.Security.SecurityCriticalAttribute> Odpovídá požadavku propojení pro úplný vztah důvěryhodnosti, ale taky ovlivňuje pravidla dědičnosti. Další informace o této změně najdete v tématu [kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Další bezpečnostní opatření, která požaduje se při použití **LinkDemand** musí být naprogramovány jednotlivě; může systém zabezpečení pomáhají s vynucením. Jakákoli chyba otevře slabé stránky zabezpečení. Všechna oprávnění, že používá váš kód musí být za implementaci další bezpečnostní pomocí následujícího kódu:  
  
-   Omezení přístupu volající kód do třídy nebo sestavení.  
  
-   Volající kód, který se zobrazí v kódu volaného a jeho volající k tomu obligating uvedení stejné zabezpečení kontroly. Například pokud píšete kód, který volá metodu, která je chráněna **LinkDemand** pro <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zadán příznak metodu také se ujistěte, **LinkDemand** (nebo **Vyžádání**, což je silnější) pro toto oprávnění. Výjimkou je, pokud váš kód používá **LinkDemand**-chráněná metoda omezeným způsobem, který se rozhodnete je bezpečné, s ohledem jiné mechanismy ochrany zabezpečení (například požadavků) ve vašem kódu. V tomto případě mimořádných volající přebírá odpovědnost za oslabení ochrany na základní kód.  
  
-   Zajištění, že volající vašeho kódu nelze přimět váš kód k volání chráněné kódu za ně. Jinými slovy volající nemůže vynutit autorizovaného kódu předat konkrétní parametry chráněného kódu nebo vrátit výsledky z něj.  
  
### <a name="interfaces-and-link-demands"></a>Rozhraní a požadavky propojení  
 Pokud virtuální metoda, vlastnost nebo událost s **LinkDemand** přepíše metodu základní třídy, metody základní třídy musí mít také stejný **LinkDemand** přepsané metody-li být účinné. Je možné, škodlivý kód pro zpětné přetypování do základního typu a volání metody základní třídy. Všimněte si, že požadavky na propojení mohou být také na sestavení, která nemají implicitně přidány <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut úrovně sestavení.  
  
 Je dobrým zvykem chránit implementace metod s požadavky propojení, když rozhraní metody mají také požadavky propojení. Mějte na paměti následující skutečnosti související požadavky propojení pomocí rozhraní:  
  
-   Pokud umístíte **LinkDemand** na veřejné metody třídy, která implementuje metodu rozhraní **LinkDemand** neuplatní, pokud následně přetypována na rozhraní a zavolejte metodu. V takovém případě vzhledem k tomu, že propojená s rozhraní, pouze **LinkDemand** rozhraní je přijmout.  
  
 Zkontrolujte následující položky pro problémy se zabezpečením:  
  
-   Požadavky na explicitní odkaz na metody rozhraní. Ujistěte se, že tyto požadavky propojení nabízejí očekávanou ochranu. Zjistěte, zda škodlivý kód může použít přetypování jsme požadavky propojení, jak je popsáno výše.  
  
-   Virtuální metody s požadavky propojení, které jsou použity.  
  
-   Typy a rozhraní, které implementují. Ty by měly použít požadavky propojení konzistentně.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
