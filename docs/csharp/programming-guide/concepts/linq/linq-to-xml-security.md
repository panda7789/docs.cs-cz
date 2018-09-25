---
title: Zabezpečení LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 0c4ee8df85d6e5c6f84947dcaaeb6875bbd687de
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027214"
---
# <a name="linq-to-xml-security-c"></a>Zabezpečení LINQ to XML (C#)
Toto téma popisuje problémy se zabezpečením související s LINQ to XML. Kromě toho poskytuje pokyny pro snížení rizik souvisejících s ohrožení zabezpečení.  
  
## <a name="linq-to-xml-security-overview"></a>Přehled LINQ to XML zabezpečení  
 Pro usnadnění práce než pro serverové aplikace s požadavky na zabezpečení přísné programování LINQ to XML slouží více. Většina scénářů XML se skládají z zpracování důvěryhodné dokumentů XML, spíše než zpracování nedůvěryhodné dokumentů XML, které jsou odeslány na server. Technologie LINQ to XML je optimalizovaná pro tyto scénáře.  
  
 Pokud je nutné zpracovat nedůvěryhodná data z neznámých zdrojů, Microsoft doporučuje, abyste použili instanci <xref:System.Xml.XmlReader> třída, která je nakonfigurovaná k filtrování známé XML útoky s cílem odepření služby (DoS).  
  
 Pokud jste nakonfigurovali <xref:System.Xml.XmlReader> ke zmírnění útoků DOS, vám pomůže tento čtečky naplnit LINQ to XML stromu a přesto využívat výhod vylepšení pro vyšší produktivitu programátorů technologie LINQ to XML. Mnoho postupů zmírnění zahrnují vytváření čtenářů, které umožňují zmírnit potíže se zabezpečením a pak vytvoření instance stromu XML pomocí nakonfigurovaného čtečky.  
  
 XML je vnitřně ohrožen útoky na dostupnost služby, protože jsou dokumenty bez vazby v velikost, hloubka, velikost název elementu a další. Bez ohledu na to komponenty, který použijete k procesu XML můžete by měla vždy připravit recyklaci doménu aplikace, pokud používá nadměrné prostředky.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Zmírnění problémů s XML, XSD, XPath a útoky XSLT  
 Technologie LINQ to XML je založena na <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Technologie LINQ to XML podporuje prostřednictvím metody rozšíření v XSD a XPath <xref:System.Xml.Schema?displayProperty=nameWithType> a <xref:System.Xml.XPath?displayProperty=nameWithType> obory názvů. Použití <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, a <xref:System.Xml.XmlWriter> třídy ve spojení s LINQ to XML, můžete vyvolat XSLT transformace stromů XML.  
  
 Pokud pracujete v méně zabezpečeném prostředí, existují některé problémy se zabezpečením, které jsou spojeny s XML a používání tříd v <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, a <xref:System.Xml.Xsl?displayProperty=nameWithType>. Tyto problémy patří, ale nejsou omezeny následující:  
  
-   XSD, XPath a XSLT jsou založené na řetězci jazyky, ve kterých můžete zadat operací, které využívají velké množství času nebo paměti. Je zodpovědností aplikace programátory, kteří přijímají řetězce XSD, XPath nebo XSLT z nedůvěryhodných zdrojů k ověření, že nejsou škodlivý, řetězce nebo k monitorování a zmírnit možnost, že vaše rozhodnutí vyzkoušet tyto řetězce může vést k nadměrné systému Spotřeba prostředků.  
  
-   Schémata XSD (včetně vložené schémat) jsou ze své podstaty ohroženy útoky na dostupnost služby; přijmout byste to by neměl schémata z nedůvěryhodných zdrojů.  
  
-   XSD a XSLT mohou obsahovat odkazy na další soubory a odkazu může vést k útokům mezi zónami a napříč doménami.  
  
-   Externí entity v DTD může vést k útokům mezi zónami a napříč doménami.  
  
-   Specifikace DTD se stát terčem útoků DOS.  
  
-   Výjimečně hloubkové dokumentů XML může představovat odmítnutí problémy se službou; můžete chtít omezit hloubky dokumentů XML.  
  
-   Nepřijmout pomocné součásti, jako například <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, a <xref:System.Xml.XmlResolver> objekty z nedůvěryhodného sestavení.  
  
-   Čtení dat za účelem zmírnění útoků velkém dokumentu.  
  
-   Bloky skriptu v šabloně stylů XSLT mohou vystavit počet útoků.  
  
-   Ověření pečlivě před sestavením dynamické výrazy XPath.  
  
## <a name="linq-to-xml-security-issues"></a>Technologie LINQ to XML problémy se zabezpečením  
 Problémy se zabezpečením v tomto tématu nejsou k dispozici v libovolném pořadí. Všechny problémy jsou důležité a mělo by se řešit podle potřeby.  
  
 Úspěšné zvýšení úrovně oprávnění dává větší kontrolu nad jeho prostředí škodlivé sestavení. Úspěšné zvýšení úrovně oprávnění útoku může způsobit zpřístupnění dat, odmítnutí služby a další.  
  
 Aplikace by neměl zpřístupnit data pro uživatele, kteří nemají oprávnění zobrazit tato data.  
  
 Útoky na dostupnost služby způsobit to, že analyzátoru XML nebo LINQ XML spotřebovat nadměrné množství času procesoru nebo paměti. Útoky na dostupnost služby, jsou považovány za méně závažná než zvýšení oprávnění pro útoky nebo zveřejnění datových útoků. Nicméně jsou důležité v případě, kdy server potřebuje ke zpracování dokumentů XML z nedůvěryhodných zdrojů.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Výjimky a chybové zprávy může odhalit dat  
 Popis chyby může odhalit dat, například dat, který se má transformovat, názvy nebo podrobnosti implementace. Chybové zprávy by neměly být vystaveny volajícím, které nejsou důvěryhodné. Měli byste zachytit všechny chyby a sestavy chyb s vlastní chybové zprávy.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nevolejte CodeAccessPermissions.Assert v obslužné rutině události  
 Sestavení může mít nižší nebo vyšší oprávnění. Sestavení, který má větší oprávnění má větší kontrolu nad počítači a jeho prostředí.  
  
 Volá-li kód v sestavení s větší oprávnění <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> v obslužné rutině události a potom XML stromu je předán škodlivé sestavení, že má omezená oprávnění, škodlivému sestavení může způsobit vyvolána událost. Protože události spouští kód, který je v sestavení s větší oprávnění, škodlivé sestavení by pak provoz se zvýšenými oprávněními.  
  
 Společnost Microsoft doporučuje, aby nikdy neměl volat <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> v obslužné rutině události.  
  
### <a name="dtds-are-not-secure"></a>Specifikace DTD jsou zabezpečení  
 Entity v DTD nejsou ze své podstaty bezpečné. Je možné, že škodlivý dokumentu XML, který obsahuje DTD způsobit analyzátor používat všechny paměti a času procesoru, odepření služby. Proto v technologii LINQ to XML, zpracování deklarace DTD je vypnuto ve výchozím nastavení. Přijmout byste to by neměl specifikace DTD z nedůvěryhodných zdrojů.  
  
 Jedním z příkladů přijetí specifikace DTD z nedůvěryhodných zdrojů je webovou aplikaci, která umožňuje uživatelům webu nahrát soubor XML, který odkazuje na DTD a DTD souboru. Při ověřování souboru třeba spustit škodlivý DTD útoku služby na serveru. Dalším příkladem přijetí specifikace DTD z nedůvěryhodných zdrojů je k odkazování DTD do sdílené síťové složky, který také umožňuje anonymní přístup k serveru FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Vyhněte se nadměrné vyrovnávací paměť přidělení  
 Vývojáři aplikací je třeba si uvědomit, že velmi velkých datových zdrojů může vést k vyčerpání prostředků a útoky na dostupnost služby.  
  
 Pokud uživatel se zlými úmysly odešle nebo odešle velké dokumentů XML, mohlo by dojít ke LINQ to XML spotřebovat nadměrné systémových prostředků. To může představovat útoku DOS. Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> vlastnost a vytvořit čtečku, která je pak omezené velikosti dokumentu, který lze načíst. Čtenáři pak použijete k vytvoření stromu XML.  
  
 Například pokud víte, že očekávaná maximální velikost dokumentů XML z nedůvěryhodného zdroje se být kratší než 50 tisíc bajtů, nastavte <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> na 100 000. To nebude encumber zpracování dokumentů XML a současně zmírnit hrozbami odepření služeb ve kterém může odeslat dokumenty, které by spotřebovávají velké množství paměti.  
  
### <a name="avoid-excess-entity-expansion"></a>Vyhněte se nadměrné Entity rozšíření  
 Jeden ze známých odmítnutí útoků služby při použití DTD je dokument, který způsobí, že rozšíření nadměrné entity. Chcete-li tomu zabránit, můžete nastavit <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> vlastnost a vytvořit čtečku, která je následně omezen počet znaků, které jsou výsledkem rozšíření entity. Čtenáři pak použijete k vytvoření stromu XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Omezení hloubky hierarchii XML  
 Jeden možný útoku DOS je při odeslání dokumentu, který má nadměrnou hloubka hierarchie. Chcete-li tomu zabránit, můžete zabalit <xref:System.Xml.XmlReader> ve své vlastní třídy, který počítá hloubku elementů. Je-li hloubka překračuje předem přiměřené úrovně, můžete ukončit zpracování dokumentu, škodlivý.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochrana proti nedůvěryhodné XmlReader nebo implementace XmlWriter  
 Správci by měli ověřit, že některé externě dodané <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> implementace mít silné názvy a jsou zaregistrovány v konfiguraci počítače. To brání škodlivým kódem ho maskují za čtečky nebo zapisovače nejde načíst.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Pravidelně uvolnit objekty XName tento odkaz  
 K ochraně proti určité druhy útoky, programátoři aplikace by měla uvolnit všechny objekty odkazující <xref:System.Xml.Linq.XName> objekt v doméně aplikace v pravidelných intervalech.  
  
### <a name="protect-against-random-xml-names"></a>Ochrana proti názvy náhodné XML  
 Aplikace, které budou data z nedůvěryhodných zdrojů byste zvážit použití <xref:System.Xml.XmlReader> , který je zabalená do vlastní kód ke kontrole možnost náhodných názvů XML a obory názvů. Pokud takové náhodných názvů XML a obory názvů jsou zjištěny, můžete aplikaci pak ukončit zpracování dokumentu, škodlivý.  
  
 Můžete chtít omezit počet názvů v daném oboru názvů (včetně názvů v žádný obor názvů) přiměřené omezení.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Poznámky jsou přístupné pro softwarové komponenty, které sdílejí technologii LINQ to XML stromu  
 Technologie LINQ to XML může vytvářet kanály zpracování, ve kterých součásti jinou aplikaci načíst, ověření, dotazování, transformace, aktualizovat a uložit data XML, který je předán mezi komponentami jako stromů XML. To může pomoct optimalizovat výkon, protože načítání a serializaci objektů do textu XML se provádí pouze na koncích kanálu. Vývojáři musí mějte na paměti, ale, že všechny poznámky a obslužné rutiny událostí vytvořených jednu komponentu je přístupný na jiné komponenty. Pokud komponenty mají různé úrovně důvěryhodnosti, to můžete vytvořit řadu ohrožení zabezpečení. A vytvořit tak zabezpečené kanály méně důvěryhodné komponentami, musí serializovat LINQ na objekty jazyka XML na XML text před předáním data pro nedůvěryhodnou součást.  
  
 Některé zabezpečení neposkytujeme modulem common language runtime (CLR). Například komponenta, která nezahrnuje soukromé třídy nemají přístup k poznámky označenými pomocí třídy. Ale poznámky můžete odstranit komponenty, které nelze číst. To lze použít jako zneužitím útoku.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
