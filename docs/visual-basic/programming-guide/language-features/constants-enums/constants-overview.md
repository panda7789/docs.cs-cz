---
title: Přehled konstant
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 9ccddfe44757c76992d641094e21ec8c2110ef83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338345"
---
# <a name="constants-overview-visual-basic"></a>Přehled konstant (Visual Basic)
Konstanta je smysluplný název, který přebírá místo čísla nebo řetězce, který se nemění. Konstanty ukládají hodnoty, které jako název implikují, zůstávají stejné během provádění aplikace. Můžete významně zlepšit čitelnost kódu a usnadnit jeho údržbu pomocí konstant. Používejte je v kódu, který obsahuje hodnoty, které se znovu objeví, nebo které závisí na určitých číslech, která se obtížně pamatují nebo nemají žádný zjevné význam.  
  
## <a name="how-to-create-and-use-constants"></a>Jak vytvořit a použít konstanty  
 Visual Basic obsahuje řadu předdefinovaných konstant, hlavně pomocí tisku a zobrazení. Můžete také vytvořit vlastní konstanty pomocí příkazu `Const` a použít stejné pokyny jako pro vytvoření názvu proměnné. Pokud je `Option Strict` `On`, musíte explicitně deklarovat typ konstanty.  
  
 Rozsah konstanty, což je sada veškerého kódu, který se na něj může odkazovat bez kvalifikovaného názvu, je stejný jako Proměnná deklarovaná ve stejném umístění. Chcete-li vytvořit konstantu, která existuje v rámci rozsahu konkrétní procedury, deklarujte ji uvnitř tohoto postupu. Chcete-li vytvořit konstantu, která je k dispozici v celé aplikaci, deklarujte ji pomocí klíčového slova `Public` v oddílu deklarace třídy.  
  
> [!NOTE]
> I když konstanty trochu připomínají proměnné, nemůžete je upravit ani přiřadit k nim nové hodnoty, jako můžete proměnné.  
  
 Konstanty, které používáte ve vašem kódu, mohou být definovány objektovým modelem pro ovládací prvky nebo komponenty, se kterými pracujete, nebo mohou být definovány uživatelem (tj. objekty, které vytvoříte sami).  
  
## <a name="compile-time-and-run-time-constants"></a>Konstanty při kompilaci a běhu  
 Konstanta v čase kompilace je vypočítána v době kompilování kódu, zatímco konstanta za běhu může být vypočítána pouze v případě, že aplikace běží. Konstanta při kompilaci bude mít stejnou hodnotu pokaždé, když je aplikace spuštěna, zatímco časová konstanta může být kdykoli změněna. Pro případy, jako jsou například hranice pole, výrazy Case nebo Inicializátory enumerátorů, jsou vyžadovány konstanty v čase kompilace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Definice|Termín|  
|---|---|  
|[Postupy: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Vysvětluje, jak použít příkaz `Const` k deklaraci konstanty a nastavení její hodnoty; deklarováním konstanty přiřadíte k hodnotě smysluplný název.|  
|[Uživatelem definované konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Popisuje, jak vytvořit vlastní konstanty, včetně informací o určení rozsahu a způsobu zamezení cyklického odkazu.|  
|[Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Poskytuje informace o způsobu, jakým kompilátor Visual Basic inicializuje konstanty, když je `Option Explicit` vypnuto.|  
|[Postupy: Seskupení souvisejících hodnot konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Ukazuje, jak seskupit konstantní hodnoty, které jsou v relaci.|  
  
## <a name="reference"></a>Odkaz  
  
|Definice|Termín|  
|---|---|  
|[Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Zobrazí konstanty předdefinované Visual Basic.|  
|[Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Popisuje příkaz `Const` a jeho použití.|  
|[Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Popisuje příkaz `Option Strict` a jeho použití.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: Inicializace proměnné pole v Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
