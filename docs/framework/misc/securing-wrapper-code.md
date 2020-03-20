---
title: Zabezpečení kódu obálky
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399908"
---
# <a name="securing-wrapper-code"></a>Zabezpečení kódu obálky
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kód obálky, zejména pokud obálka má vyšší důvěryhodnost než kód, který ji používá, můžete otevřít jedinečnou sadu slabých míst zabezpečení. Cokoli, co se provádí jménem volajícího, kde omezená oprávnění volajícího nejsou zahrnuta do příslušné kontroly zabezpečení, je potenciální slabinou, která má být zneužita.  
  
 Nikdy nepovolte něco prostřednictvím obálky, že volající nemohl udělat sám. To je zvláštní nebezpečí, když dělá něco, co zahrnuje omezenou bezpečnostní kontrolu, na rozdíl od plného zásobníku chůze poptávky. Pokud jsou zapojeny jednoúrovňové kontroly, zanesení kódu obálky mezi skutečný volající a daný prvek rozhraní API může snadno způsobit, že kontrola zabezpečení bude úspěšná, pokud by neměla, což oslabí zabezpečení.  
  
## <a name="delegates"></a>Delegáty  
 Zabezpečení delegáta se liší mezi verzemi rozhraní .NET Framework.  Tato část popisuje různé chování delegáta a související aspekty zabezpečení.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Ve verzích 1.0 a 1.1 rozhraní .NET Framework  
 Verze 1.0 a 1.1 rozhraní .NET Framework provádějí následující akce zabezpečení proti autorovi delegáta a volajícímu delegáta.  
  
- Při vytvoření delegáta jsou požadavky na propojení zabezpečení na metodu cíle delegáta prováděny proti grantové sadě tvůrce delegáta.  Nesplnění akce zabezpečení má <xref:System.Security.SecurityException>za následek .  
  
- Při vyvolání delegáta jsou provedeny všechny existující požadavky na zabezpečení volajícího delegáta.  
  
 Vždy, když <xref:System.Delegate> váš kód trvá z méně důvěryhodného kódu, který jej může volat, ujistěte se, že nepovolujete méně důvěryhodný kód eskalovat jeho oprávnění. Pokud vezmete delegáta a použijete jej později, kód, který delegáta vytvořil, není v zásobníku volání a jeho oprávnění nebudou testována, pokud se kód v delegátovi nebo pod ním pokusí o chráněnou operaci. Pokud váš kód a kód volajícího mají vyšší oprávnění než tvůrce, tvůrce může organizovat cestu volání, aniž by byl součástí zásobníku volání.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Ve verzi 2.0 a novějších verzích rozhraní .NET Framework  
 Na rozdíl od předchozích verzí verze 2.0 a novější verze rozhraní .NET Framework provádí akci zabezpečení proti delegátovi při vytvoření a volání delegáta.  
  
- Při vytvoření delegáta jsou požadavky na propojení zabezpečení na metodu cíle delegáta prováděny proti grantové sadě tvůrce delegáta.  Nesplnění akce zabezpečení má <xref:System.Security.SecurityException>za následek .  
  
- Sada grantů tvůrce delegáta je také zachycena během vytváření delegáta a uložena u delegáta.  
  
- Při vyvolání delegáta je zachycená grantová sada tvůrce delegáta nejprve vyhodnocena proti všem požadavkům v aktuálním kontextu, pokud tvůrce delegáta a volající patří do různých sestavení.  Dále jsou prováděny všechny existující požadavky na zabezpečení volajícího delegáta.  
  
## <a name="link-demands-and-wrappers"></a>Požadavky na propojení a obálky  
 Zvláštní případ ochrany s požadavky na propojení byl posílen v bezpečnostní infrastruktuře, ale je stále zdrojem možné slabosti ve vašem kódu.  
  
 Pokud plně důvěryhodný kód volá vlastnost, událost nebo metodu chráněnou [linkdemand](link-demands.md), volání proběhne úspěšně, pokud je splněna kontrola oprávnění **LinkDemand** pro volajícího. Navíc pokud plně důvěryhodný kód zpřístupňuje třídu, která přebírá název vlastnosti a volá jeho **get** přistupující objekt pomocí reflexe, toto volání **get** přistupujícího objektu úspěšné i v případě, že uživatelský kód nemá právo na přístup k této vlastnosti. Důvodem je, **že LinkDemand** kontroluje pouze bezprostřední volajícího, což je plně důvěryhodný kód. V podstatě plně důvěryhodný kód provádí privilegované volání jménem uživatelského kódu, aniž by se ujistil, že uživatelský kód má právo toto volání provést.  
  
 Chcete-li zabránit takové bezpečnostní díry, za běhu společného jazyka rozšiřuje kontrolu do úplné hojné poptávky procházení zásobníku na jakékoli nepřímé volání metody, konstruktoru, vlastnosti nebo události chráněné **LinkDemand**. Tato ochrana vznikne některé náklady na výkon a změní sémantiku kontroly zabezpečení; úplné procházení zásobníku může selhat tam, kde by prošla rychlejší jednoúrovňová kontrola.  
  
## <a name="assembly-loading-wrappers"></a>Obálky pro načítání sestavy  
 Několik metod používaných k <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>načtení spravovaného kódu, včetně načtení sestavení s důkazy volajícího. Pokud zabalíte některou z těchto metod, systém zabezpečení může použít udělení oprávnění vašeho kódu namísto oprávnění volajícího k obalu k načtení sestavení. Méně důvěryhodnému kódu byste neměli povolit načtení kódu, kterému jsou udělena vyšší oprávnění než oprávnění volajícího do obálky.  
  
 Jakýkoli kód, který má úplný vztah důvěryhodnosti nebo výrazně vyšší důvěryhodnost než potenciální volající (včetně volajícího na úrovni oprávnění k Internetu), by tímto způsobem mohl oslabit zabezpečení. Pokud váš kód má veřejnou metodu, která trvá bajt pole a předá jej **Assembly.Load**, a tím vytvořit sestavení na účet volajícího, může přerušit zabezpečení.  
  
 Tento problém se týká následujících prvků rozhraní API:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Požadavek proti LinkDemand  
 Deklarativní zabezpečení nabízí dva druhy kontrol zabezpečení, které jsou podobné, ale provádějí velmi odlišné kontroly. Měli byste pochopit oba formuláře, protože nesprávná volba může mít za následek slabé zabezpečení nebo ztrátu výkonu.  
  
 Deklarativní zabezpečení nabízí následující kontroly zabezpečení:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand>určuje procházení zásobníku zabezpečení přístupu kódu. Všichni volající v zásobníku musí mít zadané oprávnění nebo identitu předat. **Poptávka** dochází při každém volání, protože zásobníku může obsahovat různé volající. Pokud voláte metodu opakovaně, tato kontrola zabezpečení dochází pokaždé. **Poptávka** je dobrou ochranou proti lákavě útokům; neoprávněný kód se snaží dostat přes to bude detekován.  
  
- [LinkDemand](link-demands.md) se stane v době kompilace just-in-time (JIT) a zkontroluje pouze okamžité volajícího. Tato kontrola zabezpečení nekontroluje volajícího volajícího. Jakmile tato kontrola projde, neexistuje žádná další režie zabezpečení bez ohledu na to, kolikrát může volající volat. Neexistuje však ani žádná ochrana před lákavou útoky. S **LinkDemand**, jakýkoli kód, který projde testem a může odkazovat na váš kód může potenciálně přerušit zabezpečení tím, že škodlivý kód pro volání pomocí autorizovaného kódu. Proto nepoužívejte **LinkDemand,** pokud všechny možné nedostatky lze důkladně vyhnout.  
  
    > [!NOTE]
    > V rozhraní .NET Framework 4 byly požadavky <xref:System.Security.SecurityCriticalAttribute> na <xref:System.Security.SecurityRuleSet.Level2> propojení nahrazeny atributem v sestaveních. Je <xref:System.Security.SecurityCriticalAttribute> ekvivalentní požadavku na propojení pro úplnou důvěryhodnost; však ovlivňuje také pravidla dědičnosti. Další informace o této změně naleznete v [tématu Transparentní kód zabezpečení, úroveň 2](security-transparent-code-level-2.md).  
  
 Zvláštní opatření požadovaná při používání **LinkDemand** musí být naprogramována individuálně; bezpečnostní systém může pomoci s vymáháním. Každá chyba otevírá bezpečnostní slabinu. Veškerý autorizovaný kód, který používá váš kód, musí být zodpovědný za implementaci dalšího zabezpečení následujícím způsobem:  
  
- Omezení přístupu volajícího kódu ke třídě nebo sestavení.  
  
- Umístění stejné kontroly zabezpečení na volající kód, který se zobrazí na kód volány a zavazující jeho volající, aby tak učinily. Například pokud napíšete kód, který volá metodu, <xref:System.Security.Permissions.SecurityPermission> která <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> je chráněna **LinkDemand** pro s příznakem zadaným, vaše metoda by měla také **vytvořit LinkDemand** (nebo **Poptávka**, která je silnější) pro toto oprávnění. Výjimkou je, pokud váš kód používá **LinkDemand**chráněné metody v omezeném způsobem, který se rozhodnete je bezpečné, vzhledem k jiné mechanismy ochrany zabezpečení (například požadavky) ve vašem kódu. V tomto výjimečném případě volající přebírá odpovědnost za oslabení ochrany zabezpečení na základní kód.  
  
- Zajištění, že volající kódu nemůže trik váš kód do volání chráněného kódu jejich jménem. Jinými slovy volající nelze vynutit autorizovaný kód předat určité parametry chráněného kódu nebo získat výsledky zpět z něj.  
  
### <a name="interfaces-and-link-demands"></a>Rozhraní a požadavky na propojení  
 Pokud virtuální metoda, vlastnost nebo událost s **LinkDemand** přepíše metodu základní třídy, metoda základní třídy musí mít také stejnou **linkdemand** pro přepsané metody, aby byla účinná. Je možné pro škodlivý kód přetypování zpět na základní typ a volání metody základní třídy. Všimněte si také, že požadavky na propojení lze <xref:System.Security.AllowPartiallyTrustedCallersAttribute> přidat implicitně do sestavení, které nemají atribut na úrovni sestavení.  
  
 Je vhodné chránit implementace metod s požadavky na propojení, pokud mají metody rozhraní také požadavky na propojení. Všimněte si následující informace o použití požadavků na propojení s rozhraními:  
  
- Pokud umístíte **LinkDemand** na veřejnou metodu třídy, která implementuje metodu rozhraní, **LinkDemand** nebude vynucena, pokud potom přetypování do rozhraní a volání metody. V tomto případě, protože jste propojeni proti rozhraní, je dodržena pouze **LinkDemand** na rozhraní.  
  
 Zkontrolujte následující položky, pokud nejste problémy se zabezpečením:  
  
- Explicitní požadavky na propojení na metody rozhraní. Ujistěte se, že tyto požadavky na propojení nabízejí očekávanou ochranu. Zjistěte, zda škodlivý kód můžete použít přetypování obejít požadavky na propojení, jak je popsáno výše.  
  
- Virtuální metody s požadavky na propojení.  
  
- Typy a rozhraní, které implementují. Ty by měly používat požadavky na propojení konzistentně.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
