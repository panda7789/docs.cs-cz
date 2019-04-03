---
title: Přehled konstant (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841282"
---
# <a name="constants-overview-visual-basic"></a>Přehled konstant (Visual Basic)
Konstanta je smysluplný název, který probíhá číslo nebo řetězec, který se nemění. Konstanty ukládání hodnot, které, jak již název napovídá, zůstávají během spuštění aplikace. Může výrazně zlepšit čitelnost kódu a usnadňují údržbu pomocí konstanty. Jejich použití v kódu, který obsahuje hodnoty, které se zase objeví nebo, který závisí na určitých čísla, která se obtížně mějte na paměti, nebo nemají zřejmé význam.  
  
## <a name="how-to-create-and-use-constants"></a>Jak vytvořit a použít konstanty  
 Visual Basic obsahuje řadu předdefinovaných konstant, hlavně pomocí pro tisk a zobrazení. Můžete také vytvořit vlastní konstanty s `Const` příkaz pomocí stejné pokyny jako byste to udělali pro vytvoření názvu proměnné. Pokud `Option Strict` je `On`, musíte explicitně deklarovat typ konstanty.  
  
 Konstanty obor, což je sada veškerý kód, který na ni můžete odkazovat bez kvalifikace názvu je stejné jako u proměnné deklarované ve stejném umístění. Konstanta, která existuje v rámci oboru určitého postupu vytvoříte ji deklarujte v tomto postupu. Pokud chcete vytvořit konstantu, která je k dispozici v celé aplikaci, deklarujete jej s použitím `Public` – klíčové slovo v sekci prohlášení třídy.  
  
> [!NOTE]
>  Ačkoli se konstanty vypadat trochu proměnné, nelze je upravit nebo nové hodnoty jim přiřadit jako do proměnné.  
  
 Konstanty, použijte ve svém kódu může definovat objektový model pro ovládací prvky a součásti při práci s nebo mohou být uživatelem definovaný (to znamená, ty vytvoříte sami).  
  
## <a name="compile-time-and-run-time-constants"></a>Kompilace a za běhu konstanty  
 Konstantu kompilace se počítá v době, kdy kód je zkompilován, zatímco konstantu za běhu nelze vypočítat pouze když je spuštěná aplikace. Konstantu kompilace bude mít stejnou hodnotu pokaždé, když je aplikace spuštěna, zatímco konstantu za běhu se může změnit pokaždé, když. Konstanty z doby kompilace jsou požadovány pro případy, například hranice pole, výrazy case nebo enumerátoru inicializátory.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Definice|Termín|  
|---|---|  
|[Postupy: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Vysvětluje způsob používání `Const` příkazu deklarace konstanty a nastavení jeho hodnoty; deklarováním konstantu přiřadíte k hodnotě smysluplný název.|  
|[Uživatelem definované konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Popisuje, jak vytvořit vlastní konstanty, včetně informací o rozsahu a jak se vyhnout cyklické odkazy.|  
|[Datové typy konstanty a literálu](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Poskytuje informace o tom, jak kompilátor jazyka Visual Basic inicializuje konstanty při `Option Explicit` je vypnutý.|  
|[Postupy: Seskupení souvisejících hodnot konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Ukazuje, jak seskupit konstantní hodnoty, které se týkají.|  
  
## <a name="reference"></a>Odkaz  
  
|Definice|Termín|  
|---|---|  
|[Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Jsou uvedeny konstanty předdefinovaná v nástroji Visual Basic.|  
|[Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)|Popisuje `Const` příkazu a jeho použití.|  
|[Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Popisuje `Option Strict` příkazu a jeho použití.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
