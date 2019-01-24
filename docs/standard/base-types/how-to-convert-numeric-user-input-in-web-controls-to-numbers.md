---
title: 'Postupy: Převod číselného vstupu uživatele ve webových ovládacích prvcích na čísla'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c66235d866bd7c276d049d9415015dd6f9aa9fb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722358"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Postupy: Převod číselného vstupu uživatele ve webových ovládacích prvcích na čísla
Vzhledem k tomu, že na webové stránce můžete zobrazit kdekoli na světě, můžete uživatele zadat číselná data do <xref:System.Web.UI.WebControls.TextBox> ovládacího prvku v téměř neomezené množství formátů. V důsledku toho je velmi důležité určit národní prostředí a jazykovou verzi uživatele webové stránky. Při analýze uživatelský vstup, lze následně použít formátovací úmluvy určené národní prostředí a jazykovou verzi uživatele.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Pro převod číselného vstupu z ovládacího prvku TextBox webové na číslo  
  
1.  Určení, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vyplní vlastnost. Pokud není, pokračujte krokem 6.  
  
2.  Pokud je pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nastavena, získat její první prvek. První prvek určuje výchozí nebo oblíbeného jazyka a oblasti uživatele.  
  
3.  Vytvořit instanci <xref:System.Globalization.CultureInfo> upřednostňované jazykové verze objekt, který reprezentuje uživatele voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktoru.  
  
4.  Volání na buď `TryParse` nebo `Parse` metoda číselného typu, který chcete převést uživatelský vstup. Použijte přetížení `TryParse` nebo `Parse` metodou `provider` parametr a předat jí některého z následujících:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 3.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.NumberFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 3.  
  
5.  Pokud převod selže, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vrácených <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
6.  Pokud převod se nezdaří, nebo pokud řetězec pole vrácené metodou <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost nevyplněná, analýzu řetězce pomocí neutrální jazykové verze, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je na stránce dokončení kódu pro webový formulář s dotazem, aby uživatel zadal číselnou hodnotu ve <xref:System.Web.UI.WebControls.TextBox> řídit a převede na číslo. Toto číslo potom Dvojitá a zobrazit pomocí stejných pravidel formátování jako původní vstup.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Vlastnost se naplní ze názvy jazykové verze, které jsou obsaženy v `Accept-Language` záhlaví zahrnutá v jednom požadavku HTTP. Ale ne všechny prohlížeče podporují `Accept-Language` záhlaví v jejich požadavky a uživatelé mohou také potlačit hlavičky úplně. Proto je důležité mít záložní jazykovou verzi, při analýze vstup uživatele. Záložní jazykovou verzi je obvykle invariantní jazykové verze vrácené <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatelé mohou také poskytovat aplikaci Internet Explorer s názvy jazykovou verzi, zadejte do textového pole, která vytvoří možnost, že nemusí být platný název jazykové verze. Díky tomu je potřeba použít zpracování výjimek při vytváření instance <xref:System.Globalization.CultureInfo> objektu.  
  
 Při načítání z požadavku HTTP odeslané aplikací Internet Explorer, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> pole se vyplní v pořadí podle priority uživatele. První prvek v poli obsahuje název oblasti primární jazykovou verzi uživatele. Pokud pole obsahuje jakékoli další položky, aplikace Internet Explorer je libovolně přiřadí specifikátor kvality, který je oddělen od názvu jazykové verze středníkem. Například záznam pro jazykovou verzi fr-FR může mít podobu `fr-FR;q=0.7`.  
  
 Příklad volá <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktor s jeho `useUserOverride` parametr nastaven na `false` k vytvoření nového <xref:System.Globalization.CultureInfo> objektu. To zajišťuje, že pokud je název výchozí jazykové verze na serveru, název jazykové verze nové <xref:System.Globalization.CultureInfo> objekt vytvořený pomocí konstruktoru třídy obsahuje výchozí jazykové verze a neodráží všechna nastavení přepsat pomocí serveru  **Místní a jazykové nastavení** aplikace. Hodnoty z jakéhokoli přepsaného nastavení na serveru jsou pravděpodobně existuje v systému uživatele nebo se projevovat ve vstupu uživatele.  
  
 Váš kód může volat buď `Parse` nebo `TryParse` metoda číselného typu, který se uživatelovo zadání se převedou na. Opakovaná volání metody analýzy může být vyžadováno pro jedinou operaci analýzy. V důsledku toho `TryParse` metoda je lepší, protože se vrací `false` Pokud operace analýzy nezdaří. Naproti tomu zpracování opakovaných výjimek, které mohou být vyvolány `Parse` metoda může být velmi náročné návrh ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li kód zkompilovat, zkopírujte ho do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] použití modelu code-behind stránky tak, že se nahradí všechny existující kód. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Webové stránce by měl obsahovat následující prvky:  
  
-   A <xref:System.Web.UI.WebControls.Label> ovládací prvek, který se odkazuje v kódu. Nastavte jeho <xref:System.Web.UI.WebControls.TextBox.Text%2A> vlastnost "Zadejte číslo:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Nastavte jeho <xref:System.Web.UI.WebControls.Button.Text%2A> vlastnost "OK".  
  
 Změnit název třídy z `NumericUserInput` k názvu třídy, která je definována `Inherits` atribut [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky `Page` směrnice. Změňte název `NumericInput` odkaz na název definovaný podle objektu `id` atribut [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky `form` značky.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li zabránit uživatelům ve vkládání skript do HTML streamu, uživatelský vstup by nikdy zopakuje přímo zpět v odpověď serveru. Místo toho by měla být zakódován pomocí <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)
