---
title: "Zabezpečení kódu obálky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 70df7cb2f87fc2a6616d0818acdde6974bcce4d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="securing-wrapper-code"></a>Zabezpečení kódu obálky
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kód obálky, zejména kde obálku má vyšší důvěryhodnost než kód, který používá, můžete otevřít jedinečnou sadu slabá místa zabezpečení. Nic udělat jménem volající, kde omezenými oprávněními volajícího nejsou součástí odpovídající kontroly zabezpečení, je potenciální slabé místo k zneužít.  
  
 Nikdy nepovolujte něco prostřednictvím obálky, že volající nelze provádět sám sebe. Toto je speciální nebezpečí, když děláte něco, co zahrnuje kontrolu omezené zabezpečení oproti úplné procházení zásobníku. Pokud se jedná o jednu úroveň kontroly obálkového kódu mezi skutečného volajícího a prvku rozhraní API v otázku můžete snadno způsobit kontrola zabezpečení uspět, když ho by neměl, čímž oslabí zabezpečení.  
  
## <a name="delegates"></a>Delegáty  
 Delegát zabezpečení se liší mezi verzemi rozhraní .NET Framework.  Tato část popisuje různá chování delegátů a související informace o zabezpečení.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Ve verzi 1.0 a 1.1 rozhraní .NET Framework  
 Verze 1.0 a 1.1 rozhraní .NET Framework proveďte následující akce zabezpečení proti tvůrci a volající delegáta.  
  
-   Když je vytvořen delegáta, jsou požadavky na zabezpečení odkaz na cílové metody delegáta adresovat poskytnutí sady tvůrce delegáta.  Výsledkem nesplnění akce zabezpečení <xref:System.Security.SecurityException>.  
  
-   Po vyvolání delegáta jsou provedeny všechny existující požadavky zabezpečení na volajícího delegáta.  
  
 Vždy, když kód trvá <xref:System.Delegate> z méně důvěryhodného kódu, který ho může volat, ujistěte se, že méně důvěryhodného kódu pro zvýšení jeho oprávnění. Pokud přijmete delegáta a pozdější použití, kód, který vytvořili delegát není v zásobníku volání a jeho oprávnění nebudou testována, pokud kód v nebo v části delegát pokusí chráněné operace. Pokud váš kód a kód volající oprávnění vyšší než tvůrce, můžete tvůrce organizovat cestu volání, aniž by byly součástí zásobníku volání.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Ve verzi 2.0 a novější verze rozhraní .NET Framework  
 Na rozdíl od předchozích verzí verze 2.0 a novějších verzích rozhraní .NET Framework provádí akce zabezpečení vůči tvůrce delegáta při vytvoření a volá delegát.  
  
-   Když je vytvořen delegáta, jsou požadavky na zabezpečení odkaz na cílové metody delegáta adresovat poskytnutí sady tvůrce delegáta.  Výsledkem nesplnění akce zabezpečení <xref:System.Security.SecurityException>.  
  
-   Sada grant tvůrce delegáta se také zaznamenána během vytváření delegáta a uloží s delegátem.  
  
-   Po vyvolání delegáta zaznamenané udělená sada tvůrce delegáta je nejdřív porovnán s jakékoli nároky v aktuálním kontextu, pokud tvůrce delegáta a volající patří do různých sestavení.  Dále jsou provedeny všechny existující požadavky zabezpečení na volajícího delegáta.  
  
## <a name="link-demands-and-wrappers"></a>Požadavky na odkaz a obálky  
 Zvláštní ochranu případu s požadavky propojení nemá byla posílit zabezpečení infrastruktury, ale je stále zdroj možné slabé místo v kódu.  
  
 Pokud plně důvěryhodný kód volá vlastnost, události nebo metoda chráněn [LinkDemand](../../../docs/framework/misc/link-demands.md), volání bude úspěšné, pokud **LinkDemand** kontrola oprávnění pro volající je splněna. Kromě toho pokud plně důvěryhodný kód zpřístupní třídu, která má název vlastnosti a volání jeho **získat** přistupujícího objektu pomocí reflexe, toto volání **získat** přistupujícího objektu bude úspěšné, i když nemá uživatelského kódu nemá oprávnění k přístupu k této vlastnosti. Důvodem je, že **LinkDemand** kontroluje jenom bezprostředního volajícího, která je plně důvěryhodný kód. V podstatě plně důvěryhodný kód se telefonicky privilegované jménem uživatelského kódu bez a ujistěte se, zda má uživatelský kód pravé uskutečnit toto volání.  
  
 Aby se zabránilo takovým bezpečnostním rizikům, modul common language runtime rozšiřuje kontrolu do úplné procházení zásobníku vyžádaného na všechny nepřímé volání metoda, konstruktor, vlastnost nebo událostí, které jsou chráněny **LinkDemand**. Tato ochrana způsobuje náklady na výkon a změní sémantiku kontrola zabezpečení; vyžádání úplné procházení zásobníku může selhat, kde by prošla rychlejší, jednu úroveň kontroly.  
  
## <a name="assembly-loading-wrappers"></a>Obálky načítání sestavení  
 Několik metod používaných k načtení spravovaného kódu, včetně <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, načtení sestavení s důkaz volajícího. Pokud zabalením některé z těchto metod, použít systém zabezpečení vašeho kódu udělení oprávnění, místo oprávnění volajícího vaší obálky, k načtení sestavení. Měli byste méně důvěryhodný kód pro načtení kód, který má vyšší oprávnění než ty volajícího, aby vaše obálku.  
  
 Kód, který má úplný vztah důvěryhodnosti nebo důvěryhodnost výrazně vyšší než potenciální volající (včetně volající úroveň oprávnění Internetu), může oslabit zabezpečení tímto způsobem. Pokud má váš kód veřejnou metodu, která přijímá bajtové pole a předává jej do **Assembly.Load**, čímž vytvoření sestavení jménem volajícího, může porušit zabezpečení.  
  
 Tento problém se vztahuje na následující prvky rozhraní API:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Vyžádání vs. LinkDemand  
 Deklarativní zabezpečení nabízí dva druhy kontrol zabezpečení, které jsou podobné, ale provádí velmi odlišné kontroly. Protože nesprávná volba může dojít ke ztrátě slabý výkon nebo zabezpečení byste měli porozumět obou formulářů.  
  
 Deklarativní zabezpečení nabízí následující kontroly zabezpečení:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand>Určuje procházení zásobníku zabezpečení přístupu kódu. Všechny volající v zásobníku musí mít zadaný oprávnění nebo identitu předat. **Vyžádání** dochází v zásobníku může obsahovat různé volající při každém volání. Pokud při volání metody opakovaně, dojde k této kontroly zabezpečení pokaždé, když. **Vyžádání** je dobrá ochrana proti útokům typu luring; neoprávněný kód pokusu o získání přes něj bude zjištěn.  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md) dochází v době kompilace za běhu (JIT) a kontroluje jenom bezprostředního volajícího. Tato kontrola zabezpečení nekontroluje volající volajícího. Jakmile tato kontrola proběhne, neexistuje žádný další bezpečnostní režie ohledu na to, kolikrát může volající volat. Však neexistuje také žádná ochrana proti útokům typu luring. S **LinkDemand**, kód, který projde testem a může odkazovat kódu potenciálně narušit zabezpečení tím, že škodlivý kód volání pomocí oprávnění kódu. Proto nepoužívejte **LinkDemand** Pokud nebude možné slabá místa můžete zcela vyhnout.  
  
    > [!NOTE]
    >  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly nahrazeny požadavky na odkaz <xref:System.Security.SecurityCriticalAttribute> atribut <xref:System.Security.SecurityRuleSet.Level2> sestavení. <xref:System.Security.SecurityCriticalAttribute> Je ekvivalentní k požadavku na odkaz pro úplný vztah důvěryhodnosti; ale taky ovlivňuje pravidla dědičnosti. Další informace o této změně najdete v tématu [kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Vyžadováno při použití zvláštní opatření **LinkDemand** musí být naprogramováno samostatně; může zabezpečení systému, usnadní vynucení. Jakákoli chyba otevírá slabá místa zabezpečení. Všechny oprávnění kódu, používá váš kód musí být zodpovědná za implementaci dalšího zabezpečení následujícím způsobem:  
  
-   Omezení přístupu volací kód pro třídu nebo sestavení.  
  
-   Umístění stejné zabezpečení kontroly v volací kód, který se zobrazí na kód volané a obligating jeho volající Uděláte to tak. Například pokud napsat kód, který volá metodu, která je chráněný pomocí **LinkDemand** pro <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zadán příznak metodu také měli **LinkDemand** (nebo **Vyžádání**, což je silnější) pro toto oprávnění. Jedinou výjimkou je, pokud váš kód používá **LinkDemand**-chráněná metoda omezená tak, že se rozhodnete je bezpečné, daná jinými mechanismy ochrany zabezpečení (například požadavky) ve vašem kódu. V tomto případě výjimečných trvá volající odpovědnost za oslabení ochranu zabezpečení v kódu.  
  
-   Zajištění, že volající vašeho kódu nelze obelstít váš kód volání chráněného kódu jejich jménem. Jinými slovy volající nemůže vynutit kód autorizovaný k předání specifických parametrů chráněnému kódu nebo k získání výsledků z něj.  
  
### <a name="interfaces-and-link-demands"></a>Rozhraní a požadavky na odkaz  
 Pokud virtuální metoda, vlastnost nebo událost s **LinkDemand** přepíše metodu základní třídy, metoda základní třídy musí mít také stejnou **LinkDemand** pro metodu přepsaného Chcete-li být účinné. Je možné volat metodu základní třídy a převést zpět na základní typ škodlivý kód. Všimněte si, že požadavky na propojení můžete přidat i implicitně na sestavení, které nemají <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut úrovně sestavení.  
  
 Je dobrým zvykem chránit implementace metody s požadavky propojení při metody rozhraní také mít požadavky na odkaz. Vezměte na vědomí následující skutečnosti související požadavky propojení pomocí rozhraní:  
  
-   Zadáte-li **LinkDemand** na veřejné metody třídy, která implementuje metodu rozhraní **LinkDemand** se neuplatní Pokud následně převést na rozhraní a volat metodu. V takovém případě vzhledem k tomu, že jste propojili proti rozhraní pouze **LinkDemand** na rozhraní je přijmout.  
  
 Zkontrolujte následující položky pro problémy se zabezpečením:  
  
-   Požadavky na explicitní odkaz na metody rozhraní. Zajistěte, aby tyto požadavky propojení nabízejí očekávanou ochranu. Určí, zda škodlivý kód můžete použít přetypování k vyřešení požadavky propojení, jak je popsáno výše.  
  
-   Virtuální metody s požadavky na odkaz použít.  
  
-   Typy a rozhraní, které budou implementovat. Požadavky na odkaz tyto měli použít konzistentně.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
