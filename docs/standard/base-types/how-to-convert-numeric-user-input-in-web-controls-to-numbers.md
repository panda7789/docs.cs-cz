---
title: "Postupy: Převod číselného vstupu uživatele ve webových ovládacích prvcích na čísla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c93f1cda765b5f25fccddcfc27442b857262605f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Postupy: Převod číselného vstupu uživatele ve webových ovládacích prvcích na čísla
Protože na webové stránce lze zobrazit kdekoliv na světě, uživatelé mohou vložit číselná data do <xref:System.Web.UI.WebControls.TextBox> ovládacího prvku skoro neomezený počet formátů. V důsledku toho je velmi důležité určit národní prostředí a jazykovou verzi uživatele webové stránky. Pokud jste analyzovat uživatelský vstup, lze následně použít formátování konvence definované jazykovou verzi a národní prostředí uživatele.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Převést číselný vstup z ovládacího prvku webového textového pole na číslo.  
  
1.  Určení, zda pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> se naplní vlastnost. Pokud není, pokračujte krokem 6.  
  
2.  Pokud je pole řetězce vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je vyplněný, načtěte jeho první prvek. První prvek označuje výchozí nebo upřednostňovaný jazyk a oblast uživatele.  
  
3.  Vytváření instancí <xref:System.Globalization.CultureInfo> objekt, který reprezentuje uživatele upřednostňované jazykové verze voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor.  
  
4.  Volání buď `TryParse` nebo `Parse` metoda číselného typu, který chcete převést uživatele na vstup. Použijte přetížení `TryParse` nebo `Parse` metoda s `provider` parametr a předejte ji z následujících:  
  
    -   <xref:System.Globalization.CultureInfo> Objekt vytvořený v kroku 3.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Objekt, který je vrácený <xref:System.Globalization.CultureInfo.NumberFormat%2A> vlastnost <xref:System.Globalization.CultureInfo> objekt vytvořený v kroku 3.  
  
5.  Pokud převod selže, opakujte kroky 2 až 4 pro každý zbývající prvek v poli řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost.  
  
6.  Pokud převod stále nedaří nebo pole řetězců vrácené <xref:System.Web.HttpRequest.UserLanguages%2A> vlastnost je prázdná, analyzovat řetězec pomocí neutrální jazykovou verzi, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je stránka dokončení kódu pro webový formulář, který se zobrazí dotaz, aby uživatel zadal číselnou hodnotu ve <xref:System.Web.UI.WebControls.TextBox> řízení a převede jej na číslo. Toto číslo potom se používají a zobrazit pomocí stejných pravidel formátování jako původní vstup.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Vlastnost se naplní ze názvy jazykové verze, které jsou obsaženy v `Accept-Language` hlavičky požadavku HTTP. Ne všechny prohlížeče, ale patří `Accept-Language` hlavičky svých požadavků a uživatelé mohou také potlačit záhlaví úplně. Proto je důležité mít záložní jazykovou verzi, při analýze vstupu uživatele. Obvykle je záložní jazyková verze je neutrální jazykovou verzi, vrácený <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Uživatele můžete poskytnout i aplikace Internet Explorer jazykovou verzi názvy které vložili do textového pole, které vytvoří tu možnost, že názvy jazykové verze nemusí být platný. Proto je důležité použít výjimek při vytvoření instance <xref:System.Globalization.CultureInfo> objektu.  
  
 Pokud načteny z požadavku HTTP odeslaný Internet Exploreru <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> se naplní pole v pořadí podle preference uživatele. První prvek v poli obsahuje název oblasti primární jazykovou verzi uživatele. Pokud pole neobsahuje žádné další položky, Internet Explorer je libovolně přiřadí specifikátor kvality, která je oddělená od názvu jazykové verze středníkem. Položka pro jazykovou verzi fr-FR může například trvat formuláře `fr-FR;q=0.7`.  
  
 Příklad volání <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktor s jeho `useUserOverride` parametr nastaven na `false` pro vytvoření nového <xref:System.Globalization.CultureInfo> objektu. To zajišťuje, že pokud název jazykové verze je výchozí název jazykové verze na serveru nové <xref:System.Globalization.CultureInfo> objekt vytvořený pomocí konstruktoru třídy obsahuje výchozí nastavení jazykové verze a nezahrnuje žádné nastavení přepsané pomocí serveru  **Místní a jazykové nastavení** aplikace. Hodnoty z jakéhokoli přepsaného nastavení na serveru jsou pravděpodobně na uživatele systému nebo projeví ve vstupu uživatele.  
  
 Váš kód může volat buď `Parse` nebo `TryParse` metoda číselného typu, který uživatelský vstup text bude převeden na. Opakovaná volání metody analýzy může být nutný pro jednu operaci analýzy. V důsledku toho `TryParse` metoda je lepší, protože vrátí `false` Pokud selhání operace analýzy. Na rozdíl od zpracování opakovaných výjimek, které mohou být vyvolány `Parse` metoda může být velmi náročná záležitostí ve webové aplikaci.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] kódu stránky, které se nahradí všechny existující kód. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Webová stránka musí obsahovat následující prvky:  
  
-   A <xref:System.Web.UI.WebControls.Label> ovládací prvek, který není odkaz v kódu. Nastavte její <xref:System.Web.UI.WebControls.TextBox.Text%2A> vlastnost "Zadejte číslo:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> ovládací prvek s názvem `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> ovládací prvek s názvem `OKButton`. Nastavte její <xref:System.Web.UI.WebControls.Button.Text%2A> vlastnost na "OK".  
  
 Změnit název třídy z `NumericUserInput` na název třídy, která je definována `Inherits` atribut [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky `Page` – direktiva. Změňte název `NumericInput` objektu odkaz na název definované `id` atribut [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] stránky `form` značky.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Zabránit uživateli vložení skriptu do datového proudu HTML, uživatelský vstup by nikdy být opakována přímo zpět v odpovědi serveru. Místo toho by měla být zakódován pomocí <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> metoda.  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)
