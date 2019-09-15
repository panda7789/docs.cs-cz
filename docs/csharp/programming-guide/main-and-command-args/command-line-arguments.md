---
title: Argumenty příkazového řádku – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 6e6fc815ee8c2d174db12f95eed8dc72a6ef5a62
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971964"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty příkazového řádku (Průvodce programováním v C#)
Argumenty `Main` metody lze odeslat definováním metody v jednom z následujících způsobů:  
  
 [!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  
  
 [!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]  
  
> [!NOTE]
> Chcete-li povolit argumenty příkazového řádku `Main` v metodě model Windows Forms aplikace, je nutné ručně upravit `Main` signaturu v program.cs. Kód generovaný návrhářem model Windows Forms vytvoří `Main` bez vstupního parametru. Můžete také použít <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> nebo <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> pro přístup k argumentům příkazového řádku z libovolného bodu v konzole nebo v aplikaci systému Windows.  
  
 Parametr `Main` metody<xref:System.String> je pole, které představuje argumenty příkazového řádku. Obvykle určíte, zda argumenty existují, otestováním `Length` vlastnosti, například:  
  
 [!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]  
  
 Můžete také převést řetězcové argumenty na číselné typy pomocí <xref:System.Convert> třídy `Parse` nebo metody. Například následující příkaz převede `string` `long` na číslo pomocí <xref:System.Int64.Parse%2A> metody:  
  
```csharp  
long num = Int64.Parse(args[0]);  
```  
  
 Je také možné použít C# typ `long`, který aliasy: `Int64`  
  
```csharp  
long num = long.Parse(args[0]);  
```  
  
 Ke stejnému účelu můžete `Convert` použít také `ToInt64` metodu třídy:  
  
```csharp  
long num = Convert.ToInt64(s);  
```  
  
 Další informace naleznete v tématu <xref:System.Int64.Parse%2A> a <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat argumenty příkazového řádku v konzolové aplikaci. Aplikace přijímá jeden argument za běhu, převede argument na celé číslo a vypočítá faktoriál čísla. Pokud nejsou zadány žádné argumenty, aplikace vydá zprávu, která vysvětluje správné využití programu.  
  
 Chcete-li zkompilovat a spustit aplikaci z příkazového řádku, postupujte podle následujících kroků:  
  
1. Vložte následující kód do libovolného textového editoru a pak soubor uložte jako textový soubor s názvem `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]  
  
2. Z obrazovky **Start** nebo nabídky **Start** otevřete okno aplikace Visual Studio **Developer Command Prompt** a potom přejděte do složky, která obsahuje soubor, který jste právě vytvořili.  
  
3. Zadejte následující příkaz pro zkompilování aplikace.  
  
     `csc Factorial.cs`  
  
     Pokud vaše aplikace neobsahuje žádné chyby kompilace, je vytvořen spustitelný soubor s názvem `Factorial.exe` .  
  
4. Zadáním následujícího příkazu vypočítáte faktoriál čísla 3:  
  
     `Factorial 3`  
  
5. Příkaz vytvoří tento výstup:`The factorial of 3 is 6.`  
  
> [!NOTE]
> Při spuštění aplikace v aplikaci Visual Studio můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháři projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Environment?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Argumenty Main() a příkazového řádku](./index.md)
- [Postupy: Zobrazit argumenty příkazového řádku](./how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](./main-return-values.md)
- [Třídy](../classes-and-structs/classes.md)
