---
title: 'Postupy: Zobrazování lokalizovaných informací data a času webovým uživatelům'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
dev_langs:
- csharp
- vb
ms.openlocfilehash: 51142a168aba4408e6ce550a032960c4df6c3ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138735"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Postupy: Zobrazování lokalizovaných informací data a času webovým uživatelům
Vzhledem k tomu, že se webová stránka může zobrazit kdekoli na světě, operace, které analyzují a formátují hodnoty data a času, by neměly při interakci s uživatelem spoléhat na výchozí formát (což je často formát místní jazykové verze webového serveru). Místo toho webové formuláře, které zpracovávají řetězce data a času vstupem uživatele, by měly analyzovat řetězce pomocí upřednostňovanou jazykovou verzi uživatele. Podobně, data a času by se měla uživatelům zobrazit ve formátu, který odpovídá jazykové verzi uživatele. V tomto tématu se dozvíte, jak to provést.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Analýza řetězce data a času zadaný uživatelem  
  
1. Určí, zda je vyplněno pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Pokud ne, pokračujte krokem 6.  
  
2. Pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> vyplněno, načte první prvek. První prvek označuje výchozí nebo preferovaný jazyk a oblast uživatele.  
  
3. Vytvořte instanci objektu <xref:System.Globalization.CultureInfo>, který představuje upřednostňovanou jazykovou verzi uživatele voláním konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Chcete-li vyzkoušet převod, zavolejte buď `TryParse`, nebo metodu `Parse` <xref:System.DateTime> nebo <xref:System.DateTimeOffset> typu. Použijte přetížení `TryParse` nebo `Parse` metody s parametrem `provider` a předejte jí jednu z následujících možností:  
  
    - Objekt <xref:System.Globalization.CultureInfo> vytvořený v kroku 3.  
  
    - Objekt <xref:System.Globalization.DateTimeFormatInfo>, který je vrácen vlastností <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> objektu <xref:System.Globalization.CultureInfo> vytvořeného v kroku 3.  
  
5. Pokud se převod nezdařil, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vráceného vlastností <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Pokud převod stále selhává nebo pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> prázdné, analyzujte řetězec pomocí invariantní jazykové verze, která je vrácena vlastností <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Postup analýzy místního data a času požadavku uživatele  
  
1. Přidejte ovládací prvek <xref:System.Web.UI.WebControls.HiddenField> do webového formuláře.  
  
2. Vytvořte funkci JavaScriptu, která zpracovává událost `onClick` `Submit` tlačítko zápisem aktuálního data a času a posunu místního časového pásma od koordinovaného světového času (UTC) na vlastnost <xref:System.Web.UI.WebControls.HiddenField.Value%2A>. Použijte oddělovač (například středník), chcete-li oddělit dvě součásti řetězce.  
  
3. Použijte událost <xref:System.Web.UI.Control.PreRender> webového formuláře k vložení funkce do výstupního datového proudu HTML předáním textu skriptu do metody <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Připojte obslužnou rutinu události k události `onClick` `Submit`, a to zadáním názvu funkce JavaScriptu do atributu `OnClientClick` `Submit` tlačítka.  
  
5. Vytvoří obslužnou rutinu pro událost <xref:System.Web.UI.WebControls.Button.Click> tlačítka `Submit`.  
  
6. V obslužné rutině události určete, zda je vyplněno pole řetězce vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Pokud ne, pokračujte krokem 14.  
  
7. Pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> vyplněno, načte první prvek. První prvek označuje výchozí nebo preferovaný jazyk a oblast uživatele.  
  
8. Vytvořte instanci objektu <xref:System.Globalization.CultureInfo>, který představuje upřednostňovanou jazykovou verzi uživatele voláním konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
9. Předejte řetězec přiřazený k vlastnosti <xref:System.Web.UI.WebControls.HiddenField.Value%2A> do metody <xref:System.String.Split%2A> pro uložení řetězcové reprezentace místního data a času uživatele a řetězcové vyjádření posunutí místního časového pásma uživatele v samostatných prvcích pole.  
  
10. Chcete-li převést datum a čas požadavku uživatele na hodnotu <xref:System.DateTime>, zavolejte buď metodu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, nebo <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType>. Použijte přetížení metody s parametrem `provider` a předejte jí jednu z následujících možností:  
  
    - Objekt <xref:System.Globalization.CultureInfo> vytvořený v kroku 8.  
  
    - Objekt <xref:System.Globalization.DateTimeFormatInfo>, který je vrácen vlastností <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> objektu <xref:System.Globalization.CultureInfo> vytvořeného v kroku 8.  
  
11. Pokud se operace analýzy v kroku 10 nezdařila, pokračujte krokem 13. V opačném případě zavolejte metodu <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> pro převod řetězcové reprezentace posunu časového pásma uživatele na celé číslo.  
  
12. Vytvořte instanci <xref:System.DateTimeOffset> reprezentující místní čas uživatele voláním konstruktoru <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>.  
  
13. Pokud převod v kroku 10 selhává, opakujte kroky 7 až 12 pro každý zbývající prvek v poli řetězců vráceného vlastností <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
14. Pokud převod stále selhává nebo pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> prázdné, analyzujte řetězec pomocí invariantní jazykové verze, která je vrácena vlastností <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Pak opakujte kroky 7 až 12.  
  
 Výsledkem je <xref:System.DateTimeOffset> objekt, který představuje místní čas uživatele vaší webové stránky. Pak můžete určit ekvivalentní čas UTC voláním metody <xref:System.DateTimeOffset.ToUniversalTime%2A>. Ekvivalentní datum a čas na webovém serveru lze také určit voláním metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> a předáním hodnoty <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jako časového pásma pro převod času na.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje zdrojový kód HTML i kód pro webový formulář ASP.NET, který uživatele vyzve k zadání hodnoty data a času. Skript na straně klienta také zapisuje informace o místním datu a času požadavku uživatele a posunu časového pásma uživatele od času UTC po skryté pole. Tyto informace pak analyzuje Server, který vrací webovou stránku, která zobrazuje vstup uživatele. Zobrazuje také datum a čas požadavku uživatele, který používá místní čas uživatele, čas na serveru a UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Skript na straně klienta volá metodu JavaScriptu `toLocaleString`. Tím se vytvoří řetězec, který následuje za konvencí formátování národního prostředí uživatele, což je pravděpodobnější, že se na serveru bude lépe analyzovat.  
  
 Vlastnost <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> je naplněna z názvů jazykové verze, které jsou obsaženy v hlavičkách `Accept-Language` obsažených v požadavku HTTP. Některé prohlížeče ale ve svých žádostech neobsahují `Accept-Language` hlavičky a uživatelé můžou také úplně potlačit hlavičky. Díky tomu je důležité mít při analýze vstupu uživatele záložní jazykovou verzi. Záložní jazyková verze je obvykle neutrální jazyková verze vrácená funkcí <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatelé také mohou poskytnout aplikaci Internet Explorer s názvy jazykové verze, které jsou zadané v textovém poli, což vytvoří možnost, že názvy jazykových verzí nemusí být platné. Díky tomu je důležité při vytváření instance objektu <xref:System.Globalization.CultureInfo> použít zpracování výjimek.  
  
 Při načtení z požadavku HTTP odeslaného Internet Exploreru se pole <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vyplní v pořadí podle preference uživatele. První prvek v poli obsahuje název primární jazykové verze nebo oblasti uživatele. Pokud pole obsahuje nějaké další položky, Internet Explorer jim přiřadí specifikátor kvality, který je oddělen středníkem od názvu jazykové verze. Například položka pro jazykovou verzi fr-FR může mít formu `fr-FR;q=0.7`.  
  
 V příkladu je volána konstruktor <xref:System.Globalization.CultureInfo.%23ctor%2A> s parametrem `useUserOverride` nastaveným na `false` pro vytvoření nového objektu <xref:System.Globalization.CultureInfo>. Tím je zajištěno, že pokud je název jazykové verze výchozí název jazykové verze na serveru, nový objekt <xref:System.Globalization.CultureInfo> vytvořený pomocí konstruktoru třídy obsahuje výchozí nastavení jazykové verze a neodráží žádná nastavení přepsaná pomocí **regionálního serveru a Aplikace možností jazyka** . Hodnoty z jakýchkoli přepsaných nastavení na serveru pravděpodobně neexistují v systému uživatele nebo se projeví ve vstupu uživatele.  
  
 Vzhledem k tomu, že tento příklad analyzuje dvě řetězcové reprezentace data a času (jeden vstup uživatelem, druhý uložený do skrytého pole), definuje možné <xref:System.Globalization.CultureInfo> objekty, které mohou být požadovány předem. Vytvoří pole objektů <xref:System.Globalization.CultureInfo>, které je větší než počet elementů vrácených vlastností <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Potom vytvoří instanci objektu <xref:System.Globalization.CultureInfo> pro každý řetězec jazyka nebo oblasti a také vytvoří instanci objektu <xref:System.Globalization.CultureInfo>, který představuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Váš kód může zavolat buď <xref:System.DateTime.Parse%2A>, nebo metodu <xref:System.DateTime.TryParse%2A> pro převedení řetězcové reprezentace data a času na hodnotu <xref:System.DateTime>. Pro jednu operaci analýzy může být vyžadováno opakované volání metody Parse. V důsledku toho je metoda <xref:System.DateTime.TryParse%2A> lepší, protože vrátí `false`, pokud operace analýzy neproběhne úspěšně. Naproti tomu zpracování opakovaných výjimek, které mohou být vyvolány metodou <xref:System.DateTime.Parse%2A>, může být velmi nákladným umístěním ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro zkompilování kódu vytvořte webovou stránku ASP.NET bez kódu na pozadí. Pak zkopírujte příklad na webovou stránku, aby nahradil veškerý stávající kód. Webová stránka ASP.NET by měla obsahovat následující ovládací prvky:  
  
- Ovládací prvek <xref:System.Web.UI.WebControls.Label>, na který není odkazováno v kódu. Vlastnost <xref:System.Web.UI.WebControls.TextBox.Text%2A> nastavte na hodnotu zadat číslo:.  
  
- <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `DateString`.  
  
- <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Vlastnost <xref:System.Web.UI.WebControls.Button.Text%2A> nastavte na "OK".  
  
- <xref:System.Web.UI.WebControls.HiddenField> ovládací prvek s názvem `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li zabránit uživateli v vkládání skriptu do datového proudu HTML, nesmí být vstup uživatele v reakci serveru nikdy vrácen přímo. Místo toho by měl být kódován pomocí metody <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)
