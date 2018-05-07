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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63775d48ca2e11cfa121f3b7aeaff708d86e50de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Postupy: Zobrazování lokalizovaných informací data a času webovým uživatelům
Protože na webové stránce lze zobrazit kdekoliv na světě, analyzovat a formátuje hodnoty data a času operací neměli spoléhat na výchozí formát (což je nejčastěji formát jazykové verze místní webový server) při interakci s uživatelem. Místo toho by měla webových formulářů, které zpracovávají datum a čas uživatelský vstup řetězce analyzovat řetězců pomocí upřednostňované jazykové verze uživatele. Podobně data a času, které má být zobrazena uživateli ve formátu, který vyhovuje jazykovou verzi uživatele. Toto téma ukazuje, jak to udělat.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Analyzovat data a času řetězce uživatelský vstup  
  
1.  Určení, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> se naplní vlastnost. Pokud není, pokračujte krokem 6.  
  
2.  Pokud je pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je vyplněný, načtěte jeho první prvek. První prvek označuje výchozí nebo upřednostňovaný jazyk a oblast uživatele.  
  
3.  Vytváření instancí <xref:System.Globalization.CultureInfo> objekt, který reprezentuje uživatele upřednostňované jazykové verze voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor.  
  
4.  Volání buď `TryParse` nebo `Parse` metodu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pro pokus o převod. Použijte přetížení `TryParse` nebo `Parse` metoda s `provider` parametr a předejte ji z následujících:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 3.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 3.  
  
5.  Pokud převod selže, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
6.  Pokud převod stále nedaří nebo pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je prázdná, analyzovat řetězec pomocí neutrální jazykovou verzi, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Analyzovat místní datum a čas požadavku uživatele  
  
1.  Přidat <xref:System.Web.UI.WebControls.HiddenField> řízení webového formuláře.  
  
2.  Vytvoření funkce JavaScript, která zpracovává `onClick` události `Submit` tlačítko napsáním aktuální datum a čas a posun místního časového pásma z koordinovaný světový čas (UTC) k <xref:System.Web.UI.WebControls.HiddenField.Value%2A> vlastnost. K oddělení dvou součástí řetězec použijte oddělovač (např. středníkem).  
  
3.  Použití webového formuláře <xref:System.Web.UI.Control.PreRender> událost vložení funkce do kódu HTML výstupního datového proudu předáním text skriptu <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> metoda.  
  
4.  Obslužné rutiny události pro připojení `Submit` tlačítka `onClick` událostí tím, že poskytuje název funkce JavaScript `OnClientClick` atribut `Submit` tlačítko.  
  
5.  Vytvořte obslužnou rutinu pro `Submit` tlačítka <xref:System.Web.UI.WebControls.Button.Click> událostí.  
  
6.  V obslužné rutině události určit, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> se naplní vlastnost. Pokud není, pokračujte krokem 14.  
  
7.  Pokud je pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je vyplněný, načtěte jeho první prvek. První prvek označuje výchozí nebo upřednostňovaný jazyk a oblast uživatele.  
  
8.  Vytváření instancí <xref:System.Globalization.CultureInfo> objekt, který reprezentuje uživatele upřednostňované jazykové verze voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor.  
  
9. Předejte řetězec přiřazený k <xref:System.Web.UI.WebControls.HiddenField.Value%2A> vlastnost, která má <xref:System.String.Split%2A> metoda k uložení řetězcovou reprezentaci uživatele místní datum a čas a řetězcovou reprezentaci posunu místního časového pásma uživatele do samostatných prvků pole.  
  
10. Volání buď <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> způsobů, jak převést datum a čas požadavku uživatele na <xref:System.DateTime> hodnotu. Použijte přetížení metody s `provider` parametr a předejte ji z následujících:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 8.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 8.  
  
11. Pokud se nezdaří operace analýzy v kroku 10, přejděte ke kroku 13. Jinak volání <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> způsobů, jak převést řetězcovou reprezentaci posun časového pásma uživatele na celé číslo.  
  
12. Vytváření instancí <xref:System.DateTimeOffset> voláním představující uživatele místního času <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktor.  
  
13. Pokud převod v kroku 10 selže, opakujte kroky 7 až 12 pro každý zbývající prvek v poli řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
14. Pokud převod stále nedaří nebo pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je prázdná, analyzovat řetězec pomocí neutrální jazykovou verzi, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Opakujte kroky 7 až 12.  
  
 Výsledkem je, <xref:System.DateTimeOffset> objekt, který představuje místní čas uživatele webové stránky. Poté můžete určit odpovídající čas standardu UTC voláním <xref:System.DateTimeOffset.ToUniversalTime%2A> metoda. Můžete také určit ekvivalentní datum a čas na vašem webovém serveru při volání <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda a předáním hodnoty <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jako časové pásmo převést čas.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje zdrojový kód HTML a kód pro formuláře ASP.NET Web, který požádá uživatele o zadání hodnoty data a času. Klientský skript také do skryté pole zapisuje informace na místní datum a čas požadavku uživatele a posun časového pásma uživatele od času UTC. Tyto informace se potom analyzovat serverem, která vrátí hodnotu na webové stránce, která zobrazuje vstup uživatele. Také zobrazuje datum a čas požadavku uživatele pomocí místní čas uživatele, na server a UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Klientský skript volá JavaScript `toLocaleString` metoda. Tímto se vytvoří řetězec, který následuje konvencí formátování národního prostředí uživatele, který je více pravděpodobně možné úspěšně analyzovat na serveru.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Vlastnost se naplní ze názvy jazykové verze, které jsou obsaženy v `Accept-Language` hlavičky požadavku HTTP. Ne všechny prohlížeče, ale patří `Accept-Language` hlavičky svých požadavků a uživatelé mohou také potlačit záhlaví úplně. Proto je důležité mít záložní jazykovou verzi, při analýze vstupu uživatele. Obvykle je záložní jazyková verze je neutrální jazykovou verzi, vrácený <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatele můžete poskytnout i aplikace Internet Explorer jazykovou verzi názvy které vložili do textového pole, které vytvoří tu možnost, že názvy jazykové verze nemusí být platný. Proto je důležité použít výjimek při vytvoření instance <xref:System.Globalization.CultureInfo> objektu.  
  
 Pokud načteny z požadavku HTTP odeslaný Internet Exploreru <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> se naplní pole v pořadí podle preference uživatele. První prvek v poli obsahuje název oblasti primární jazykovou verzi uživatele. Pokud pole neobsahuje žádné další položky, Internet Explorer je libovolně přiřadí specifikátor kvality, která je oddělená od názvu jazykové verze středníkem. Položka pro jazykovou verzi fr-FR může například trvat formuláře `fr-FR;q=0.7`.  
  
 Příklad volání <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktor s jeho `useUserOverride` parametr nastaven na `false` pro vytvoření nového <xref:System.Globalization.CultureInfo> objektu. To zajišťuje, že pokud název jazykové verze je výchozí název jazykové verze na serveru nové <xref:System.Globalization.CultureInfo> objekt vytvořený pomocí konstruktoru třídy obsahuje výchozí nastavení jazykové verze a nezahrnuje žádné nastavení přepsané pomocí serveru  **Místní a jazykové nastavení** aplikace. Hodnoty z jakéhokoli přepsaného nastavení na serveru jsou pravděpodobně na uživatele systému nebo projeví ve vstupu uživatele.  
  
 Protože v tomto příkladu analyzuje dvě řetězcové vyjádření data a času (jeden vstup uživatele, druhý uložený na skrytá pole), definuje možné <xref:System.Globalization.CultureInfo> objekty, které mohou být vyžadovány předem. Vytvoří pole <xref:System.Globalization.CultureInfo> objekty, které je větší než počet elementů vrácený <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vlastnost. Poté se vytvoří instance <xref:System.Globalization.CultureInfo> objekt pro každý řetězec jazyka nebo oblasti a také se vytvoří instance <xref:System.Globalization.CultureInfo> objekt, který reprezentuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Váš kód může volat buď <xref:System.DateTime.Parse%2A> nebo <xref:System.DateTime.TryParse%2A> metoda převést uživatele řetězec představující datum a čas <xref:System.DateTime> hodnotu. Opakovaná volání metody analýzy může být nutný pro jednu operaci analýzy. V důsledku toho <xref:System.DateTime.TryParse%2A> metoda je lepší, protože vrátí `false` Pokud selhání operace analýzy. Na rozdíl od zpracování opakovaných výjimek, které mohou být vyvolány <xref:System.DateTime.Parse%2A> metoda může být velmi náročná záležitostí ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, vytvořit [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webové stránky bez kódu na pozadí. Zkopírujte příklad do webové stránky, tak, aby se nahradí všechny existující kód. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Webová stránka musí obsahovat následující prvky:  
  
-   A <xref:System.Web.UI.WebControls.Label> ovládací prvek, který není odkaz v kódu. Nastavte její <xref:System.Web.UI.WebControls.TextBox.Text%2A> vlastnost "Zadejte číslo:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Nastavte její <xref:System.Web.UI.WebControls.Button.Text%2A> vlastnost na "OK".  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> ovládací prvek s názvem `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Zabránit uživateli vložení skriptu do datového proudu HTML, uživatelský vstup by nikdy být opakována přímo zpět v odpovědi serveru. Místo toho by měla být zakódován pomocí <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metoda.  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)
