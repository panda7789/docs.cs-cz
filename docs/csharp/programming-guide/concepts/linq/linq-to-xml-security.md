---
title: LINQ do zabezpečení XML (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 5b7eb815b058cba008f1db2cf683c8934c19b743
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73423374"
---
# <a name="linq-to-xml-security-c"></a>LINQ do zabezpečení XML (C#)
Toto téma popisuje problémy se zabezpečením spojené s LINQ do XML. Kromě toho poskytuje některé pokyny pro zmírnění expozice zabezpečení.  
  
## <a name="linq-to-xml-security-overview"></a>Přehled zabezpečení LINQ to XML  
 LINQ to XML je určen spíše pro pohodlí programování než pro serverové aplikace s přísnými požadavky na zabezpečení. Většina scénářů XML se skládá ze zpracování důvěryhodných dokumentů XML, nikoli ze zpracování nedůvěryhodných dokumentů XML, které jsou odeslány na server. LINQ na XML je optimalizován pro tyto scénáře.  
  
 Pokud je nutné zpracovat nedůvěryhodná data z neznámých zdrojů, společnost Microsoft doporučuje použít instanci <xref:System.Xml.XmlReader> třídy, která byla nakonfigurována k odfiltrování známých útoků xml odmítnutí služby (DoS).  
  
 Pokud jste nakonfigurovali útok <xref:System.Xml.XmlReader> na odmítnutí služby, můžete pomocí této čtečky naplnit linq do stromu XML a stále těžit z vylepšení produktivity programátora LINQ na XML. Mnoho zmírňujících technik zahrnuje vytváření čtenářů, které jsou nakonfigurovány ke zmírnění problému se zabezpečením, a vytvoření instance stromu XML prostřednictvím nakonfigurované čtečky.  
  
 Jazyk XML je vnitřně zranitelný vůči útokům odmítnutí služby, protože dokumenty jsou neohraničené velikostí, hloubkou, velikostí názvu prvku a dalšími. Bez ohledu na součást, kterou používáte ke zpracování xml, měli byste být vždy připraveni recyklovat doménu aplikace, pokud používá nadměrné prostředky.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Zmírnění útoků XML, XSD, XPath a XSLT  
 LINQ na XML <xref:System.Xml.XmlReader> je <xref:System.Xml.XmlWriter>postaven na a . LINQ to XML podporuje XSD a XPath prostřednictvím rozšiřujících metod v <xref:System.Xml.Schema?displayProperty=nameWithType> oborech názvů a. <xref:System.Xml.XPath?displayProperty=nameWithType> Pomocí <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>a <xref:System.Xml.XmlWriter> třídy ve spojení s LINQ do XML, můžete vyvolat XSLT transformovat stromy XML.  
  
 Pokud pracujete v méně zabezpečeném prostředí, existuje řada problémů se zabezpečením, které <xref:System.Xml?displayProperty=nameWithType>jsou <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType>spojeny <xref:System.Xml.Xsl?displayProperty=nameWithType>s jazykem XML a použitím tříd v oblasti , , a . Mezi tyto problémy patří mimo jiné následující:  
  
- XSD, XPath a XSLT jsou jazyky založené na řetězecích, ve kterých můžete určit operace, které spotřebovávají hodně času nebo paměti. Je odpovědností programátorů aplikací, kteří používají řetězce XSD, XPath nebo XSLT z nedůvěryhodných zdrojů, aby ověřili, že řetězce nejsou škodlivé, nebo aby monitorovali a zmírňovali možnost, že vyhodnocení těchto řetězců povede k nadměrnému systému spotřeby zdrojů.  
  
- Schémata XSD (včetně inline schémat) jsou ze své podstaty ohrožena útoky odmítnutí služby; schémata byste neměli přijímat z nedůvěryhodných zdrojů.  
  
- XSD a XSLT mohou obsahovat odkazy na jiné soubory a tyto odkazy mohou vést k útokům mezi zónami a mezi doménami.  
  
- Externí entity v DTD mohou mít za následek útoky mezi zónami a mezi doménami.  
  
- DTD jsou náchylné k útokům odmítnutí služby.  
  
- Výjimečně hluboké dokumenty XML mohou představovat problémy s odmítnutím služby. můžete chtít omezit hloubku dokumentů XML.  
  
- Nepřijímejte podpůrné součásti, <xref:System.Xml.NameTable> <xref:System.Xml.XmlNamespaceManager>například <xref:System.Xml.XmlResolver> , a objekty, z nedůvěryhodných sestavení.  
  
- Čtení dat v blocích pro zmírnění útoků velkých dokumentů.  
  
- Bloky skriptů v šablonách stylů XSLT mohou vystavit řadu útoků.  
  
- Před vytvořením dynamických výrazů XPath pečlivě ověřte.  
  
## <a name="linq-to-xml-security-issues"></a>Linq na problémy se zabezpečením XML  
 Problémy se zabezpečením v tomto tématu nejsou uvedeny v libovolném pořadí. Všechny otázky jsou důležité a měly by být podle potřeby řešeny.  
  
 Úspěšné zvýšení oprávnění útoku dává škodlivé sestavení větší kontrolu nad jeho prostředí. Úspěšné zvýšení oprávnění útoku může mít za následek zpřístupnění dat, odmítnutí služby a další.  
  
 Aplikace by neměly sdělovat údaje uživatelům, kteří nejsou oprávněni tyto údaje zobrazit.  
  
 Útoky odmítnutí služby způsobí, že analyzátor XML nebo LINQ na XML spotřebovávají nadměrné množství paměti nebo času procesoru. Útoky s cílem odepření služby jsou považovány za méně závažné než zvýšení oprávnění útoky nebo zpřístupnění útoků dat. Jsou však důležité ve scénáři, kde server potřebuje zpracovávat dokumenty XML z nedůvěryhodných zdrojů.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Výjimky a chybové zprávy mohou odhalit data  
 Popis chyby může odhalit data, jako jsou například transformovaná data, názvy souborů nebo podrobnosti implementace. Chybové zprávy by neměly být vystaveny volajícím, kteří nejsou důvěryhodní. Měli byste zachytit všechny chyby a hlásit chyby s vlastní mise.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nevolat CodeAccessPermissions.Assert v obslužné rutině události  
 Sestavení může mít menší nebo větší oprávnění. Sestavení, které má větší oprávnění, má větší kontrolu nad počítačem a jeho prostředími.  
  
 Pokud kód v sestavení s <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> většími oprávněními volá v obslužné rutině události a potom je strom XML předán škodlivému sestavení, které má omezená oprávnění, může škodlivé sestavení způsobit vyvolání události. Vzhledem k tomu, že událost spustí kód, který je v sestavení s většími oprávněními, škodlivé sestavení by pak pracovat se zvýšenými oprávněními.  
  
 Společnost Microsoft doporučuje nikdy <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> volat obslužnou rutinu události.  
  
### <a name="dtds-are-not-secure"></a>DTD nejsou zabezpečené  
 Entity v DTD nejsou ze své podstaty nejsou zabezpečené. Je možné, že škodlivý dokument XML, který obsahuje DTD, způsobí, že analyzátor použije veškerou paměť a čas procesoru, což způsobí útok odmítnutí služby. Proto v LINQ na XML je zpracování DTD ve výchozím nastavení vypnuto. Neměli byste přijímat DTD z nedůvěryhodných zdrojů.  
  
 Jedním z příkladů přijetí DTD z nedůvěryhodných zdrojů je webová aplikace, která umožňuje webovým uživatelům nahrát soubor XML, který odkazuje na soubor DTD a DTD. Po ověření souboru může škodlivý DTD spustit útok odmítnutí služby na serveru. Dalším příkladem přijetí DTD z nedůvěryhodných zdrojů je odkaz na DTD na sdílené síťové složce, která také umožňuje anonymní přístup FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Vyhněte se nadměrnému přidělení vyrovnávací paměti  
 Vývojáři aplikací by si měli být vědomi toho, že extrémně velké zdroje dat mohou vést k vyčerpání prostředků a útokům odmítnutí služby.  
  
 Pokud uživatel se zlými úmysly odešle nebo odešle velmi velký dokument XML, může to způsobit, že LINQ do XML spotřebuje nadměrné systémové prostředky. To může představovat útok odmítnutí služby. Chcete-li tomu zabránit, <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> můžete nastavit vlastnost a vytvořit čtečku, která je pak omezena ve velikosti dokumentu, který může načíst. Potom pomocí čtečky k vytvoření stromu XML.  
  
 Pokud například víte, že maximální očekávaná velikost dokumentů XML pocházejících z nedůvěryhodného zdroje bude <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> menší než 50 bajtů, nastavená na 100 000. To nezatíží vaše zpracování dokumentů XML a zároveň to zmírní hrozby odmítnutí služby, kde mohou být nahrány dokumenty, které by spotřebovávaly velké množství paměti.  
  
### <a name="avoid-excess-entity-expansion"></a>Vyhněte se nadměrnému rozšíření entity  
 Jeden ze známých útoků odmítnutí služby při použití DTD je dokument, který způsobuje nadměrné rozšíření entity. Chcete-li tomu zabránit, <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> můžete nastavit vlastnost a vytvořit čtečku, která je pak omezena v počtu znaků, které vyplývají z rozšíření entity. Potom pomocí čtečky k vytvoření stromu XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Omezení hloubky hierarchie XML  
 Jedním z možných útoku odmítnutí služby je při odeslání dokumentu, který má nadměrnou hloubku hierarchie. Chcete-li tomu zabránit, <xref:System.Xml.XmlReader> můžete zabalit ve vlastní třídě, která počítá hloubku prvků. Pokud hloubka překročí předem stanovenou přiměřenou úroveň, můžete ukončit zpracování škodlivého dokumentu.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochrana před nedůvěryhodnými implementacemi XmlReader nebo XmlWriter  
 Správci by měli ověřit, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> zda všechny externě zadané nebo implementace mají silné názvy a byly registrovány v konfiguraci počítače. Tím zabráníte načtení škodlivého kódu maskovaného jako čtenář nebo zapisovatel.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Pravidelně volné objekty, které odkazují na XName  
 Chcete-li chránit před určitými druhy útoků, programátoři <xref:System.Xml.Linq.XName> aplikací by měli pravidelně uvolnit všechny objekty, které odkazují na objekt v doméně aplikace.  
  
### <a name="protect-against-random-xml-names"></a>Chránit před náhodnými názvy XML  
 Aplikace, které přebírají data z <xref:System.Xml.XmlReader> nedůvěryhodných zdrojů, by měly zvážit použití souboru, který je zabalen do vlastního kódu, ke kontrole možnosti náhodných názvů XML a jmenných prostorů. Pokud jsou tyto náhodné názvy XML a obory názvů zjištěny, aplikace pak může ukončit zpracování škodlivého dokumentu.  
  
 Počet názvů v libovolném oboru názvů (včetně názvů v žádném oboru názvů) můžete omezit na přiměřené omezení.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Poznámky jsou přístupné softwarovým součástem, které sdílejí linq se stromem XML  
 Linq na XML lze použít k vytvoření kanálů zpracování, ve kterých různé součásti aplikace načítají, ověřují, dotazují, transformují, aktualizují a ukládají data XML předávaná mezi součástmi jako stromy XML. To může pomoci optimalizovat výkon, protože režie načítání a serializace objektů na text XML se provádí pouze na koncích kanálu. Vývojáři si však musí být vědomi toho, že všechny poznámky a obslužné rutiny událostí vytvořené jednou komponentou jsou přístupné ostatním součástem. To může vytvořit řadu chyb zabezpečení, pokud součásti mají různé úrovně důvěryhodnosti. Chcete-li vytvořit zabezpečené kanály mezi méně důvěryhodnými součástmi, je nutné serializovat linq na objekty XML na text XML před předáním dat nedůvěryhodné součásti.  
  
 Některé zabezpečení poskytuje za běhu common jazyka (CLR). Například součást, která neobsahuje soukromou třídu, nemůže přistupovat k poznámkám, které tato třída zamísťuje. Poznámky však mohou být odstraněny součástmi, které je nemohou číst. Tohle by mohlo být použito jako znemanipulacní útok.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka (LINQ to XML) (C#)](linq-to-xml-overview.md)
