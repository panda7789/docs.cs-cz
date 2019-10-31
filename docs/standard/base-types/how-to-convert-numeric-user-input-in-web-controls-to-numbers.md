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
ms.openlocfilehash: 78ba284ad2e75b39c0fb1001b0f65b48c519dbb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140109"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Postupy: Převod číselného vstupu uživatele ve webových ovládacích prvcích na čísla
Vzhledem k tomu, že se webová stránka může zobrazit kdekoli na světě, můžou uživatelé zadávat číselná data do ovládacího prvku <xref:System.Web.UI.WebControls.TextBox> v téměř neomezeném počtu formátů. V důsledku toho je velmi důležité určit národní prostředí a jazykovou verzi uživatele webové stránky. Při analýze vstupu uživatele můžete použít konvence formátování definované národním prostředím a jazykovou verzí uživatele.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Převod číselného vstupu z ovládacího prvku webový ovládací prvek TextBox na číslo  
  
1. Určí, zda je vyplněno pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Pokud ne, pokračujte krokem 6.  
  
2. Pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> vyplněno, načte první prvek. První prvek označuje výchozí nebo preferovaný jazyk a oblast uživatele.  
  
3. Vytvořte instanci objektu <xref:System.Globalization.CultureInfo>, který představuje upřednostňovanou jazykovou verzi uživatele voláním konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Zavolejte buď `TryParse`, nebo metodu `Parse` číselného typu, na který chcete převést vstup uživatele na. Použijte přetížení `TryParse` nebo `Parse` metody s parametrem `provider` a předejte jí jednu z následujících možností:  
  
    - Objekt <xref:System.Globalization.CultureInfo> vytvořený v kroku 3.  
  
    - Objekt <xref:System.Globalization.NumberFormatInfo>, který je vrácen vlastností <xref:System.Globalization.CultureInfo.NumberFormat%2A> objektu <xref:System.Globalization.CultureInfo> vytvořeného v kroku 3.  
  
5. Pokud se převod nezdařil, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vráceného vlastností <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Pokud převod stále selhává nebo pokud je pole řetězců vrácené vlastností <xref:System.Web.HttpRequest.UserLanguages%2A> prázdné, analyzujte řetězec pomocí invariantní jazykové verze, která je vrácena vlastností <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je úplná Stránka s kódem na pozadí pro webový formulář, který vyzve uživatele k zadání číselné hodnoty v ovládacím prvku <xref:System.Web.UI.WebControls.TextBox> a převede ho na číslo. Toto číslo se pak zdvojnásobí a zobrazí se pomocí stejných pravidel formátování jako u původního vstupu.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 Vlastnost <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> je naplněna z názvů jazykové verze, které jsou obsaženy v hlavičkách `Accept-Language` obsažených v požadavku HTTP. Některé prohlížeče ale ve svých žádostech neobsahují `Accept-Language` hlavičky a uživatelé můžou také úplně potlačit hlavičky. Díky tomu je důležité mít při analýze vstupu uživatele záložní jazykovou verzi. Záložní jazyková verze obvykle představuje invariantní jazykovou verzi vrácenou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatelé také mohou poskytnout aplikaci Internet Explorer s názvy jazykové verze, které jsou zadané v textovém poli, což vytvoří možnost, že názvy jazykových verzí nemusí být platné. Díky tomu je důležité při vytváření instance objektu <xref:System.Globalization.CultureInfo> použít zpracování výjimek.  
  
 Při načtení z požadavku HTTP odeslaného Internet Exploreru se pole <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> vyplní v pořadí podle preference uživatele. První prvek v poli obsahuje název primární jazykové verze nebo oblasti uživatele. Pokud pole obsahuje nějaké další položky, Internet Explorer jim přiřadí specifikátor kvality, který je oddělen středníkem od názvu jazykové verze. Například položka pro jazykovou verzi fr-FR může mít formu `fr-FR;q=0.7`.  
  
 V příkladu je volána konstruktor <xref:System.Globalization.CultureInfo.%23ctor%2A> s parametrem `useUserOverride` nastaveným na `false` pro vytvoření nového objektu <xref:System.Globalization.CultureInfo>. Tím je zajištěno, že pokud je název jazykové verze výchozí název jazykové verze na serveru, nový objekt <xref:System.Globalization.CultureInfo> vytvořený pomocí konstruktoru třídy obsahuje výchozí nastavení jazykové verze a neodráží žádná nastavení přepsaná pomocí **regionálního serveru a Aplikace možností jazyka** . Hodnoty z jakýchkoli přepsaných nastavení na serveru pravděpodobně neexistují v systému uživatele nebo se projeví ve vstupu uživatele.  
  
 Váš kód může zavolat buď `Parse`, nebo metodu `TryParse` číselného typu, na který bude vstup uživatele převeden. Pro jednu operaci analýzy může být vyžadováno opakované volání metody Parse. V důsledku toho je metoda `TryParse` lepší, protože vrátí `false`, pokud operace analýzy neproběhne úspěšně. Naproti tomu zpracování opakovaných výjimek, které mohou být vyvolány metodou `Parse`, může být velmi nákladným umístěním ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat kód, zkopírujte jej na stránku ASP.NET kódu na pozadí, aby nahradil veškerý stávající kód. Webová stránka ASP.NET by měla obsahovat následující ovládací prvky:  
  
- Ovládací prvek <xref:System.Web.UI.WebControls.Label>, na který není odkazováno v kódu. Vlastnost <xref:System.Web.UI.WebControls.TextBox.Text%2A> nastavte na hodnotu zadat číslo:.  
  
- <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `NumericString`.  
  
- <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Vlastnost <xref:System.Web.UI.WebControls.Button.Text%2A> nastavte na "OK".  
  
 Změňte název třídy z `NumericUserInput` na název třídy, která je definována atributem `Inherits` direktivy `Page` stránky ASP.NET. Změňte název odkazu na objekt `NumericInput` na název definovaný atributem `id` značky `form` stránky ASP.NET.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li zabránit uživateli v vkládání skriptu do datového proudu HTML, nesmí být vstup uživatele v reakci serveru nikdy vrácen přímo. Místo toho by měl být kódován pomocí metody <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)
