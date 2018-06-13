---
title: Technologie LINQ to XML zabezpečení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: 3f75377502b30b03090bb2a5fe720faf4e12a028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655455"
---
# <a name="linq-to-xml-security-visual-basic"></a>Technologie LINQ to XML zabezpečení (Visual Basic)
Toto téma popisuje problémy se zabezpečením přidružené technologie LINQ to XML. Kromě toho obsahuje některé pokyny pro minimalizaci ohrožení zabezpečení.  
  
## <a name="linq-to-xml-security-overview"></a>Technologie LINQ to XML Přehled zabezpečení  
 Technologie LINQ to XML je určeno více pro programování pohodlí než pro serverové aplikace s požadavky na přísné zabezpečení. Většina scénářů XML obsahovat zpracování důvěryhodných dokumentů XML, nikoli zpracování nedůvěryhodné dokumentů XML, které jsou odeslány na server. Technologie LINQ to XML je optimalizovaná pro tyto scénáře.  
  
 Pokud je nutné zpracovat nedůvěryhodné data z neznámých zdrojů, Microsoft doporučuje používat instanci <xref:System.Xml.XmlReader> třídy, který byl nakonfigurován pro odfiltrování známé XML útoků DoS (DoS).  
  
 Pokud jste nakonfigurovali <xref:System.Xml.XmlReader> zmírnit útoků DOS, můžete použít tento čtečky naplnit LINQ to XML stromu a využívat výhod vylepšení produktivitu programátory technologie LINQ to XML. Mnoho postupů zmírnění zahrnují vytváření čtenářů, které jsou nakonfigurované ke zmírnění problém zabezpečení a pak vytváření instancí strom XML prostřednictvím nakonfigurované čtečky.  
  
 XML je vnitřně bude zranitelný vůči útoku DOS, protože dokumenty jsou bez vazby v velikost, hloubku, velikost názvu elementu a další. Bez ohledu na komponentu, který použijete k procesu XML jste měli vždy připravte se na recyklovat doménu aplikace, pokud využívá příliš prostředků.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Zmírnění dopadů XML, XSD, XPath a útoky XSLT  
 Technologie LINQ to XML je založena na <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Technologie LINQ to XML podporuje XSD a XPath prostřednictvím metody rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> a <xref:System.Xml.XPath?displayProperty=nameWithType> obory názvů. Pomocí <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, a <xref:System.Xml.XmlWriter> třídy ve spojení s technologie LINQ to XML, můžete vyvolat XSLT k transformaci stromy XML.  
  
 Pokud pracujete v méně zabezpečeném prostředí, existují určité problémy zabezpečení, které jsou spojeny s XML a použití třídy v <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, a <xref:System.Xml.Xsl?displayProperty=nameWithType>. Tyto problémy patří, ale nejsou omezeny následující:  
  
-   XSD, XPath a XSLT jsou založené na řetězcích jazyky, ve kterých můžete zadat operace, které využívají spoustu času nebo paměti. Je zodpovědností aplikace programátory, kteří přijímají řetězce XSD, XPath nebo XSLT z nedůvěryhodných zdrojů k ověření, že řetězce nejsou škodlivý, nebo k monitorování a zmírnit možnost, že vyhodnocování tyto řetězce povede k nadměrnému systému spotřeby prostředků.  
  
-   XSD schémata (včetně vložená schémata) jsou ze své podstaty bude zranitelný vůči útoku DoS; schémata z nedůvěryhodných zdrojů nesmí přijmout.  
  
-   XSD a XSLT mohou obsahovat odkazy na další soubory a tyto odkazy můžete vést útoky mezi zóny a napříč doménami.  
  
-   Externí entity v specifikace DTD může způsobit útoky mezi zóny a napříč doménami.  
  
-   Specifikace DTD se stát terčem útoku DOS.  
  
-   Výjimečně hloubkové dokumentů XML může představovat odmítnutí problémů služby; můžete chtít omezit hloubka dokumentů XML.  
  
-   Nepřijímají podpůrné součásti, jako například <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, a <xref:System.Xml.XmlResolver> objekty z nedůvěryhodné sestavení.  
  
-   Čtení dat v blocích pro snížit riziko útoků velké dokumentu.  
  
-   Bloky skriptu v stylů XSLT můžete vystavit číslo útoků.  
  
-   Ověření pečlivě před vytvořením dynamické výrazech XPath.  
  
## <a name="linq-to-xml-security-issues"></a>Technologie LINQ to XML problémy se zabezpečením  
 Problémy se zabezpečením v tomto tématu nejsou přítomny v libovolném pořadí. Všechny problémy jsou důležité a mělo by se řešit podle potřeby.  
  
 Úspěšné zvýšení oprávnění dává větší kontrolu nad jeho prostředí škodlivé sestavení. Úspěšné zvýšení úrovně oprávnění útoku může vést k úniku dat, odmítnutí služby a další.  
  
 Aplikace neměl zpřístupnit data pro uživatele, kteří nejste oprávněni zobrazit tato data.  
  
 Útoků DoS způsobit analyzátor XML nebo LINQ XML využívat nadměrné množství paměti nebo doba využití procesoru. Útoků DOS se považují za méně závažné než zvýšení oprávnění útoků nebo zpřístupnění dat útoků. Jsou to ale důležité v případě, kdy je server ke zpracování dokumentů XML z nedůvěryhodných zdrojů.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Výjimky a chybové zprávy může odhalit dat  
 Popis chyby může odhalit dat, jako je transformovat data, soubor názvy nebo podrobnosti implementace. Chybové zprávy by neměly být vystaveny pro volající, které nejsou důvěryhodné. Měli catch všechny chyby a chyby sestavy s vlastními vlastní chybové zprávy.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nevolejte CodeAccessPermissions.Assert v obslužné rutině události  
 Sestavení může mít menší nebo větší oprávnění. Sestavení, který má větší oprávnění má větší kontrolu nad počítačem a jeho prostředí.  
  
 Volá-li kód v sestavení s větší oprávnění <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> obslužné rutiny události, a potom soubor XML stromu předaný škodlivé sestavení, má omezená oprávnění, škodlivý sestavení může způsobit, že má být aktivována událost. Vzhledem k tomu, že událost spustí kód, který je v sestavení s větší oprávnění, škodlivý sestavení by pak operační se zvýšenými oprávněními.  
  
 Společnost Microsoft doporučuje, aby nikdy volat <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> v obslužné rutině události.  
  
### <a name="dtds-are-not-secure"></a>Specifikace DTD jsou zabezpečení  
 Entity v specifikace DTD jsou ze své podstaty není bezpečné. Je možné pro škodlivý dokument XML, který obsahuje DTD způsobí analyzátor používat všechny paměti a času procesoru, odepření služby. Proto v technologii LINQ to XML DTD zpracování je vypnutý ve výchozím nastavení. Specifikace DTD z nedůvěryhodných zdrojů nesmí přijmout.  
  
 Jedním z příkladů přijetí specifikace DTD z nedůvěryhodných zdrojů je webovou aplikaci, která umožňuje uživatelům webové nahrát soubor XML, který odkazuje na DTD a souboru DTD. Při ověřování souboru by mohl spustit škodlivý DTD útoku DOS na vašem serveru. Dalším příkladem přijetí specifikace DTD z nedůvěryhodných zdrojů je tak, aby odkazovaly DTD ve sdílené síťové složce, která také umožňuje anonymní přístup k serveru FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Vyhněte se nadměrné vyrovnávací paměti přidělení  
 Vývojáři aplikací měli vědět, že velmi rozsáhlých datových zdrojů může vést k vyčerpání prostředků a útoku DOS.  
  
 Pokud uživatel se zlými úmysly odešle nebo odešle velké dokument XML, může se stát, LINQ to XML využívat nadměrné systémové prostředky. To může představovat útoku DOS. Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> vlastnost a vytvořit čtečku, která je pak omezenou velikost dokumentu, který může načíst. Čtečka pak použijete k vytvoření stromové struktuře XML.  
  
 Například pokud víte, že maximální očekávaná velikost dokumentů XML pocházejících z nedůvěryhodného zdroje budou méně než 50 tisíc bajtů, nastavte <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> na 100 000. To nebude encumber zpracování dokumentů XML a současně ho bude zmírnit útok na dostupnost služby hrozeb kde může nahrát dokumenty, které by využívat velké množství paměti.  
  
### <a name="avoid-excess-entity-expansion"></a>Vyhněte se nadměrné Entity rozšíření  
 Jeden z známých útoků DOS při použití DTD je dokument, který způsobí, že rozšíření nadměrné entity. Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> vlastnost a vytvořit čtečku, který je pak omezená počtu znaků, které jsou výsledkem rozšíření entity. Čtečka pak použijete k vytvoření stromové struktuře XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Maximální hloubka hierarchii XML  
 Jeden možné útoku DOS je při odeslání dokumentu, který má nadměrné hloubku hierarchie. Chcete-li tomu zabránit, můžete zabalit <xref:System.Xml.XmlReader> v vlastní třídu, která udává hloubka elementů. Pokud je hloubkou překročí předem určený přiměřenou úroveň, můžete ukončit zpracování škodlivý dokumentu.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochrana proti nedůvěryhodné XmlReader nebo XmlWriter implementace  
 Správci by měli ověřit, že všechny externě zadaný <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> implementace silné názvy a byly zaregistrovány v konfiguraci počítače. Tím se zabrání škodlivý kód vydávají za čtečka nebo zápisu u načítá.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Pravidelně volné objekty XName tento odkaz  
 K ochraně proti určitými typy útoků, by měl programátorům aplikací bez všechny objekty, které odkazují <xref:System.Xml.Linq.XName> objekt v doméně aplikace v pravidelných intervalech.  
  
### <a name="protect-against-random-xml-names"></a>Ochrana proti názvy náhodných XML  
 Aplikace, které potřebují dat z nedůvěryhodných zdrojů byste měli zvážit použití <xref:System.Xml.XmlReader> tedy zabalené v vlastní kód ke kontrole možnost náhodných názvů XML a obory názvů. Pokud nejsou zjištěny tyto náhodných názvů XML a obory názvů, můžete aplikaci pak ukončit zpracování škodlivý dokumentu.  
  
 Můžete chtít omezit počet názvy v daném oboru názvů (včetně názvů v žádné oboru názvů) přiměřených finančních omezení.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Poznámky jsou přístupné pro softwarové komponenty, které sdílejí LINQ to XML stromu  
 Technologie LINQ to XML lze použít k vytvoření kanálů pro zpracování ve kterých součásti jinou aplikaci načíst, ověření, dotaz, transformace, aktualizovat a uložit data XML, který je předán mezi součástmi jako XML stromy. To může pomoct optimalizace výkonu, protože režii načítání a serializaci objektů textu XML se provádí pouze na konci kanálu. Vývojáři musí Mějte ale na, zda jsou přístupné pro ostatní součásti poznámky a obslužné rutiny událostí vytvořené jedna součást. Pokud komponenty mají různé úrovně důvěryhodnosti, to můžete vytvořit řada chyb. K vytvoření zabezpečeného kanály napříč méně součástí důvěryhodný, musí serializovat LINQ na objekty XML do textu XML před jejím odesláním do nedůvěryhodné komponenty.  
  
 Modul CLR (CLR) zajišťuje některé zabezpečení. Například komponenty, která nezahrnuje Soukromá třída nemůže získat přístup s klíči třídy poznámky. Poznámky však lze odstranit součásti, které nelze přečíst. Tento soubor lze použít jako zneužitím útoku.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
