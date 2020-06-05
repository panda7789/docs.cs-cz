---
title: Zabezpečení LINQ to XML
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: 2be3e2df81af046035832794766f3317e1e96e35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368527"
---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ to XML zabezpečení (Visual Basic)
Toto téma popisuje problémy se zabezpečením související s LINQ to XML. Kromě toho poskytuje některé pokyny ke zmírnění ohrožení zabezpečení.  
  
## <a name="linq-to-xml-security-overview"></a>Přehled zabezpečení LINQ to XML  
 LINQ to XML je navrženější pro usnadnění programování než pro aplikace na straně serveru s přísnými požadavky na zabezpečení. Většina scénářů XML sestává z zpracování důvěryhodných dokumentů XML namísto zpracování nedůvěryhodných dokumentů XML, které jsou odeslány na server. LINQ to XML je pro tyto scénáře optimalizována.  
  
 Pokud je nutné zpracovat nedůvěryhodná data z neznámých zdrojů, společnost Microsoft doporučuje použít instanci <xref:System.Xml.XmlReader> třídy, která byla konfigurována pro vyfiltrování známých útoků DOS (Denial of Service) typu XML.  
  
 Pokud jste nakonfigurovali <xref:System.Xml.XmlReader> pro zmírnění útoků s cílem odepření služby, můžete pomocí tohoto čtecího zařízení naplnit LINQ to XML stromové struktuře a nadále využívat vylepšení aplikace LINQ to XML pro programátory. Mnoho technik zmírnění rizik zahrnuje vytváření čtecích zařízení, která jsou nakonfigurovaná pro zmírnění potíží se zabezpečením, a následné vytvoření instance stromu XML pomocí nakonfigurovaného čtecího modulu.  
  
 KÓD XML je vnitřně zranitelný vůči útokům DOS (Denial of Service), protože jsou neohraničené velikosti, hloubky, velikosti názvu elementu a další. Bez ohledu na komponentu, kterou použijete ke zpracování XML, byste měli vždy být připraveni k recyklaci domény aplikace, pokud používá nadměrné prostředky.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Zmírnění útoků XML, XSD, XPath a XSLT  
 LINQ to XML je postaven na <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> . LINQ to XML podporuje XSD a XPath prostřednictvím rozšiřujících metod v <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType> oborech názvů a. Pomocí <xref:System.Xml.XmlReader> tříd, <xref:System.Xml.XPath.XPathNavigator> a <xref:System.Xml.XmlWriter> ve spojení s LINQ to XML lze vyvolat XSLT pro transformaci stromů XML.  
  
 Pokud pracujete v méně zabezpečeném prostředí, je k dispozici řada problémů se zabezpečením, které jsou spojeny s XML a používání tříd v systémech <xref:System.Xml?displayProperty=nameWithType> , <xref:System.Xml.Schema?displayProperty=nameWithType> , a <xref:System.Xml.XPath?displayProperty=nameWithType> <xref:System.Xml.Xsl?displayProperty=nameWithType> . Mezi tyto problémy patří mimo jiné tyto problémy:  
  
- XSD, XPath a XSLT jsou jazyky založené na řetězci, ve kterých můžete zadat operace, které spotřebovávají spoustu času nebo paměti. Je odpovědností programátorů aplikací, kteří přijímají řetězce XSD, XPath nebo XSLT z nedůvěryhodných zdrojů, aby ověřili, že tyto řetězce nejsou škodlivé, nebo pokud chcete monitorovat a zmírnit riziko, že vyhodnocování těchto řetězců vede k nadměrné spotřebě systémových prostředků.  
  
- Schémata XSD (včetně vložených schémat) jsou z vlastního podstaty zranitelná útokům DOS (Denial of Service). neměli byste přijímat schémata z nedůvěryhodných zdrojů.  
  
- XSD a XSLT můžou zahrnovat odkazy na jiné soubory a takové odkazy můžou vést k útokům mezi zónami a mezi doménami.  
  
- Externí entity v definicích DTD můžou vést k útokům mezi zónami a mezi doménami.  
  
- Specifikace DTD jsou zranitelné kvůli útokům DOS (Denial of Service).  
  
- Mimořádně hluboké dokumenty XML mohou představovat odepření problémů se službou. Možná budete chtít omezit hloubku dokumentů XML.  
  
- Nepřijímejte podpůrné komponenty, jako jsou <xref:System.Xml.NameTable> , <xref:System.Xml.XmlNamespaceManager> a <xref:System.Xml.XmlResolver> objekty, z nedůvěryhodných sestavení.  
  
- Umožňuje číst data v blocích a zmírnit tak útoky na velké dokumenty.  
  
- Bloky skriptu v šablonách stylů XSLT můžou vystavovat řadu útoků.  
  
- Než začnete vytvářet dynamické výrazy XPath, ověřte pečlivě.  
  
## <a name="linq-to-xml-security-issues"></a>Problémy se zabezpečením LINQ to XML  
 Problémy se zabezpečením v tomto tématu nejsou uvedeny v žádném konkrétním pořadí. Všechny problémy jsou důležité a měly by se řešit podle potřeby.  
  
 Po úspěšném zvýšení oprávnění útoků získá škodlivější sestavení lepší kontrolu nad jeho prostředím. Úspěšné zvýšení úrovně oprávnění může mít za následek zveřejnění dat, odmítnutí služby a další.  
  
 Aplikace by neměly vyzradit data uživatelům, kteří nemají oprávnění k zobrazení těchto dat.  
  
 Útoky na útok DOS způsobí, že analyzátor XML nebo LINQ to XML spotřebovat nadměrné množství paměti nebo času procesoru. Útoky DoS (Denial of Service) se považují za méně závažnou než zvýšení úrovně oprávnění nebo odhalení útoků s daty. Jsou však důležité v situaci, kdy server potřebuje zpracovat dokumenty XML z nedůvěryhodných zdrojů.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Výjimky a chybové zprávy můžou odhalit data.  
 Popis chyby může odhalit data, jako jsou transformovaná data, názvy souborů nebo podrobnosti implementace. Volajícím, kteří nejsou důvěryhodní, by neměly být vystavené chybové zprávy. Měli byste zachytit všechny chyby a ohlásit chyby s vlastními chybovými zprávami.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nevolejte CodeAccessPermissions. Assert v obslužné rutině události  
 Sestavení může mít méně nebo více oprávnění. Sestavení, které má větší oprávnění, má větší kontrolu nad počítačem a jeho prostředími.  
  
 Pokud kód v sestavení s větším oprávněním volá <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> v obslužné rutině události a poté je strom XML předán škodlivému sestavení, které má omezená oprávnění, může škodlivá sestavení způsobit vyvolání události. Vzhledem k tomu, že událost spouští kód, který je v sestavení s větším oprávněním, pak by škodlivá sestavení byla provozována se zvýšenými oprávněními.  
  
 Společnost Microsoft doporučuje, abyste nikdy nevolali <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> v obslužné rutině události.  
  
### <a name="dtds-are-not-secure"></a>Soubory DTD nejsou zabezpečené  
 Entity v definicích DTD jsou ze své podstaty nezabezpečené. V případě škodlivého dokumentu XML, který obsahuje DTD, je možné, že analyzátor bude používat veškerou paměť a čas procesoru, což by způsobilo útok na útok DoS (Denial of Service). Proto je v LINQ to XML zpracování DTD ve výchozím nastavení vypnuté. Nepřijímáte specifikace DTD z nedůvěryhodných zdrojů.  
  
 Jedním z příkladů přijetí souborů DTD z nedůvěryhodných zdrojů je webová aplikace, která umožňuje webovým uživatelům odeslat soubor XML, který odkazuje na DTD a soubor DTD. Po ověření souboru může škodlivá deklarace DTD na vašem serveru spustit útok na útok DoS (Denial of Service). Dalším příkladem přijetí souborů DTD z nedůvěryhodných zdrojů je odkazování na DTD v síťové sdílené složce, který taky povoluje anonymní přístup FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Vyhnout se nadměrnému přidělení vyrovnávací paměti  
 Vývojáři aplikací by měli vědět, že extrémně velké zdroje dat můžou vést k vyčerpání prostředků a útokům na dostupnost služby.  
  
 Pokud uživatel se zlými úmysly odesílá nebo nahraje velmi velký dokument XML, může to způsobit, že LINQ to XML spotřebovat nadměrné systémové prostředky. To může znamenat útok na útok DoS (Denial of Service). Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> vlastnost a vytvořit čtecí modul, který je pak omezen velikostí dokumentu, který může načíst. Pak pomocí čtecího zařízení vytvoříte strom XML.  
  
 Pokud například víte, že maximální očekávaná velikost dokumentů XML přicházejících z nedůvěryhodného zdroje bude menší než 50 tis bajtů, nastavte <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> na 100 000. Encumber se tím, že se vaše zpracování dokumentů XML neprojeví a zároveň se tím sníží hrozby útoku DOS, kde mohou být nahrány dokumenty, které spotřebují velké objemy paměti.  
  
### <a name="avoid-excess-entity-expansion"></a>Vyhnout se nadměrnému rozšíření entit  
 Jedním ze známých útoků DOS (Denial of Service) při použití DTD je dokument, který způsobuje nadměrné rozšíření entit. Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> vlastnost a vytvořit čtecí modul, který je poté omezen počtem znaků, které jsou výsledkem rozšíření entity. Pak pomocí čtecího zařízení vytvoříte strom XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Omezit hloubku hierarchie XML  
 Jedním z možných útoků DOS (Denial of Service) je odeslání dokumentu, který má nadměrnou hloubku hierarchie. Chcete-li tomu zabránit, můžete zabalit do <xref:System.Xml.XmlReader> vlastní třídy, která počítá hloubku prvků. Pokud hloubka překročí předem stanovenou rozumnou úroveň, můžete ukončit zpracování škodlivého dokumentu.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Chránit před nedůvěryhodnými implementacemi XmlReader nebo XmlWriter  
 Správci by měli ověřit, že všechny externě dodávané <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> implementace mají silné názvy a jsou zaregistrované v konfiguraci počítače. Tím se zabrání načtení škodlivého kódu jako čtecí modul nebo zapisovač.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Periodické bezplatné objekty, které odkazují na XName  
 Pro ochranu proti určitým druhům útoků by Programátori aplikací měli v pravidelných intervalech uvolnit všechny objekty, které odkazují na <xref:System.Xml.Linq.XName> objekt v doméně aplikace.  
  
### <a name="protect-against-random-xml-names"></a>Ochrana proti náhodným názvům XML  
 Aplikace, které přijímají data z nedůvěryhodných zdrojů, by měly zvážit použití <xref:System.Xml.XmlReader> , který je zabalen do vlastního kódu, aby zkontroloval možnost náhodných názvů XML a oborů názvů. Pokud jsou zjištěny tyto náhodné názvy XML a obory názvů, může aplikace ukončit zpracování škodlivého dokumentu.  
  
 Můžete chtít omezit počet názvů v libovolném daném oboru názvů (včetně názvů v žádném oboru názvů) na rozumný limit.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Poznámky jsou přístupné komponentami softwaru, které sdílejí strom LINQ to XML.  
 LINQ to XML lze použít k sestavování zpracovávaných kanálů, ve kterých různé komponenty aplikace načítají, ověřují, dotazují, transformují, aktualizují a ukládají data XML, která jsou předána mezi komponentami jako stromy XML. To může přispět k optimalizaci výkonu, protože režie načítání a serializace objektů do textu XML je provedena pouze na koncích kanálu. Vývojáři si ale musí být vědomi, že všechny poznámky a obslužné rutiny událostí, které vytvořila jedna součást, jsou přístupné pro jiné komponenty. To může vytvořit několik ohrožení zabezpečení, pokud komponenty mají různé úrovně důvěryhodnosti. Chcete-li vytvářet zabezpečené kanály napříč méně důvěryhodnými komponentami, je nutné před předáním dat do nedůvěryhodné součásti serializovat objekty LINQ to XML do textu XML.  
  
 Určité zabezpečení je zajištěno modulem CLR (Common Language Runtime). Například komponenta, která nezahrnuje soukromou třídu, nemůže přistupovat k poznámkám, které tato třída používá. Poznámky však lze odstranit komponentami, které je nemohou číst. Tento způsob se dá použít jako útok na manipulaci.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
