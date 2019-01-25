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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d46b2634096cf71701458ca7ecb6f66a01ebffbe
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857655"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Postupy: Zobrazování lokalizovaných informací data a času webovým uživatelům
Vzhledem k tomu, že na webové stránce můžete zobrazit kdekoli na světě, operací, které analyzovat a formátování hodnot data a času, neměli byste tedy spoléhat na výchozí formát (což je nejčastěji formátu jazykové verze místní webový server) při interakci s uživatelem. Webové formuláře, které zpracovávají datum a čas uživatelský vstup řetězce místo toho by se měly analyzovat řetězců pomocí upřednostňované jazykové verze uživatele. Podobně data a času má být zobrazena na uživatele ve formátu, který odpovídá na jazykovou verzi uživatele. Toto téma ukazuje, jak to provést.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Analyzovat datum a čas řetězce uživatelský vstup  
  
1.  Určení, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vyplní vlastnost. Pokud není, pokračujte krokem 6.  
  
2.  Pokud je pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nastavena, získat její první prvek. První prvek určuje výchozí nebo oblíbeného jazyka a oblasti uživatele.  
  
3.  Vytvořit instanci <xref:System.Globalization.CultureInfo> upřednostňované jazykové verze objekt, který reprezentuje uživatele voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktoru.  
  
4.  Volání na buď `TryParse` nebo `Parse` metodu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> typ zkuste převod. Použijte přetížení `TryParse` nebo `Parse` metodou `provider` parametr a předat jí některého z následujících:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 3.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 3.  
  
5.  Pokud převod selže, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vrácených <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
6.  Pokud převod se nezdaří, nebo pokud řetězec pole vrácené metodou <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nevyplněná, analýzu řetězce pomocí neutrální jazykové verze, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Analýza místního data a času žádost uživatele  
  
1.  Přidat <xref:System.Web.UI.WebControls.HiddenField> ovládací prvek webového formuláře.  
  
2.  Funkce JavaScriptu, která zpracovává vytvořit `onClick` události `Submit` napsáním aktuální datum a čas a posun místního časového pásma od koordinovaného světového času (UTC) na tlačítko <xref:System.Web.UI.WebControls.HiddenField.Value%2A> vlastnost. Používejte oddělovač (např. středníkem) oddělují dva řetězce.  
  
3.  Použití webového formuláře <xref:System.Web.UI.Control.PreRender> událost vložení funkce do kódu HTML předáním text tohoto skriptu do výstupního datového proudu <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> metody.  
  
4.  Připojte obslužné rutiny události `Submit` tlačítka `onClick` události zadáním názvu funkce JavaScriptu, která se `OnClientClick` atribut `Submit` tlačítko.  
  
5.  Vytvořte obslužnou rutinu pro `Submit` tlačítka <xref:System.Web.UI.WebControls.Button.Click> událostí.  
  
6.  V obslužné rutině události určit, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vyplní vlastnost. Pokud není, pokračujte krokem 14.  
  
7.  Pokud je pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nastavena, získat její první prvek. První prvek určuje výchozí nebo oblíbeného jazyka a oblasti uživatele.  
  
8.  Vytvořit instanci <xref:System.Globalization.CultureInfo> upřednostňované jazykové verze objekt, který reprezentuje uživatele voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktoru.  
  
9. Předat řetězec přiřazené <xref:System.Web.UI.WebControls.HiddenField.Value%2A> vlastnost <xref:System.String.Split%2A> metody pro ukládání řetězcovou reprezentaci uživatele místní data a času a řetězcovou reprezentaci posunu místního časového pásma uživatele v samostatných prvků pole.  
  
10. Volání na buď <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> způsobů, jak převést datum a čas žádosti uživatele <xref:System.DateTime> hodnotu. Použijte přetížení metody `provider` parametr a předat buď z následujících akcí:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 8.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 8.  
  
11. Pokud se nezdaří operace analýzy v kroku 10, přejděte ke kroku 13. V opačném případě volat <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> způsobů, jak převést řetězcové vyjádření posun časového pásma uživatele na celé číslo.  
  
12. Vytvořit instanci <xref:System.DateTimeOffset> , která představuje uživatele místní čas voláním <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktoru.  
  
13. Pokud převod v kroku 10 selže, opakujte kroky 7 až 12 pro každý zbývající prvek v poli řetězců vrácených <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
14. Pokud převod se nezdaří, nebo pokud řetězec pole vrácené metodou <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nevyplněná, analýzu řetězce pomocí neutrální jazykové verze, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Opakujte kroky 7 až 12.  
  
 Výsledkem je <xref:System.DateTimeOffset> objekt, který představuje místní čas uživatele webové stránky. Můžete určit ekvivalentní UTC pomocí volání <xref:System.DateTimeOffset.ToUniversalTime%2A> metody. Můžete také určit odpovídá datu a času na vašem webovém serveru pomocí volání <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda a předáním hodnoty <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> jako časové pásmo, čas převést.  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje zdrojový kód HTML a kód pro webový formulář ASP.NET, která vyzve uživatele k zadání hodnoty data a času. Skript na straně klienta také zapisuje informace o místní datum a čas žádost uživatele a posun časového pásma uživatele od času UTC do skryté pole. Tyto informace se pak analyzovat serverem, které vrací webové stránky, která zobrazuje vstup uživatele. Také zobrazí datum a čas pomocí místní čas uživatele, na server a standardem UTC žádost uživatele.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Skript na straně klienta vyvolá JavaScript `toLocaleString` metody. To vytvoří řetězec, který dodržuje konvence formátování národního prostředí uživatele, který je větší pravděpodobnost úspěšně analyzovat na serveru.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Vlastnost se naplní ze názvy jazykové verze, které jsou obsaženy v `Accept-Language` záhlaví zahrnutá v jednom požadavku HTTP. Ale ne všechny prohlížeče podporují `Accept-Language` záhlaví v jejich požadavky a uživatelé mohou také potlačit hlavičky úplně. Proto je důležité mít záložní jazykovou verzi, při analýze vstup uživatele. Záložní jazykovou verzi je obvykle invariantní jazykové verze vrácené <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatelé mohou také poskytovat aplikaci Internet Explorer s názvy jazykovou verzi, zadejte do textového pole, která vytvoří možnost, že nemusí být platný název jazykové verze. Díky tomu je potřeba použít zpracování výjimek při vytváření instance <xref:System.Globalization.CultureInfo> objektu.  
  
 Při načítání z požadavku HTTP odeslané aplikací Internet Explorer, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> pole se vyplní v pořadí podle priority uživatele. První prvek v poli obsahuje název oblasti primární jazykovou verzi uživatele. Pokud pole obsahuje jakékoli další položky, aplikace Internet Explorer je libovolně přiřadí specifikátor kvality, který je oddělen od názvu jazykové verze středníkem. Například záznam pro jazykovou verzi fr-FR může mít podobu `fr-FR;q=0.7`.  
  
 Příklad volá <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktor s jeho `useUserOverride` parametr nastaven na `false` k vytvoření nového <xref:System.Globalization.CultureInfo> objektu. To zajišťuje, že pokud je název výchozí jazykové verze na serveru, název jazykové verze nové <xref:System.Globalization.CultureInfo> objekt vytvořený pomocí konstruktoru třídy obsahuje výchozí jazykové verze a neodráží všechna nastavení přepsat pomocí serveru  **Místní a jazykové nastavení** aplikace. Hodnoty z jakéhokoli přepsaného nastavení na serveru jsou pravděpodobně existuje v systému uživatele nebo se projevovat ve vstupu uživatele.  
  
 Protože v tomto příkladu analyzuje dva řetězcové vyjádření data a času (jeden vstup uživatele, ostatní uložené do skryté pole), definuje možné <xref:System.Globalization.CultureInfo> objekty, které mohou být vyžadovány předem. Vytvoří pole <xref:System.Globalization.CultureInfo> objekty, které je větší než počet prvků vrácených <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vlastnost. Poté vytvoří instanci <xref:System.Globalization.CultureInfo> objekt pro každý řetězec jazyka a oblasti a také vytvoří instanci <xref:System.Globalization.CultureInfo> objekt, který reprezentuje <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Váš kód může volat buď <xref:System.DateTime.Parse%2A> nebo <xref:System.DateTime.TryParse%2A> metody pro převod uživatele řetězec představující datum a čas <xref:System.DateTime> hodnotu. Opakovaná volání metody analýzy může být vyžadováno pro jedinou operaci analýzy. V důsledku toho <xref:System.DateTime.TryParse%2A> metoda je lepší, protože vrátí `false` Pokud operace analýzy nezdaří. Naproti tomu zpracování opakovaných výjimek, které mohou být vyvolány <xref:System.DateTime.Parse%2A> metoda může být velmi náročné návrh ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li kód zkompilovat, vytvořte [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] webové stránky bez kódu na pozadí. Zkopírujte příkladu do webové stránky, takže nahradí všechny existující kód. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Webové stránce by měl obsahovat následující prvky:  
  
-   A <xref:System.Web.UI.WebControls.Label> ovládací prvek, který se odkazuje v kódu. Nastavte jeho <xref:System.Web.UI.WebControls.TextBox.Text%2A> vlastnost "Zadejte číslo:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Nastavte jeho <xref:System.Web.UI.WebControls.Button.Text%2A> vlastnost "OK".  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> ovládací prvek s názvem `DateInfo`.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li zabránit uživatelům ve vkládání skript do HTML streamu, uživatelský vstup by nikdy zopakuje přímo zpět v odpověď serveru. Místo toho by měla být zakódován pomocí <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)
