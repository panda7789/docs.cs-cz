---
title: Argumenty příkazového řádku - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 32dcfc8da52fc623473a1cc234e710463f8d28be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722696"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty příkazového řádku (Průvodce programováním v C#)
Argumenty můžete poslat `Main` metoda definováním metody jedním z následujících způsobů:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Chcete-li povolit argumenty příkazového řádku `Main` metodu v aplikaci Windows Forms, je nutné ručně upravit podpis `Main` v souboru program.cs. Vytvoří kód generovaný návrhářem formulářů Windows `Main` bez vstupního parametru. Můžete také použít <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> nebo <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> pro přístup k argumenty příkazového řádku z libovolného bodu v konzole nebo v aplikaci Windows.  
  
 Parametr `Main` je metoda <xref:System.String> pole, které představuje argumenty příkazového řádku. Obvykle zjistíte, zda existují argumenty testováním `Length` vlastnosti, například:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Můžete také převést řetězcové argumenty pro číselné typy s použitím <xref:System.Convert> třídy nebo `Parse` metody. Například následující výraz převede `string` k `long` čísla pomocí <xref:System.Int64.Parse%2A> metody:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Je také možné použít typ jazyka C# `long`, které aliasy `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Můžete také použít `Convert` metoda třídy `ToInt64` na stejnou věc udělat:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Další informace naleznete v tématu <xref:System.Int64.Parse%2A> a <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat argumenty příkazového řádku v konzolové aplikaci. Aplikace přijímá jeden argument za běhu, převede argument na celé číslo a vypočítá faktoriál čísla. Pokud nejsou dodány žádné argumenty, aplikace vydá zprávu, která vysvětluje správné použití programu.  
  
 Kompilace a spuštění aplikace z příkazového řádku, postupujte podle těchto kroků:  
  
1.  Vložte následující kód do libovolného textového editoru a uložte soubor jako textový soubor s názvem `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Z **Start** obrazovky nebo **Start** nabídky, otevřete sadu Visual Studio **Developer Command Prompt** okna a pak přejděte do složky, která obsahuje soubor, který jste právě vytvořit.  
  
3.  Zadejte následující příkaz pro kompilaci aplikace.  
  
     `csc Factorial.cs`  
  
     Pokud vaše aplikace neobsahuje žádné chyby během kompilace, spustitelný soubor, který je pojmenován `Factorial.exe` se vytvoří.  
  
4.  Zadejte následující příkaz pro výpočet faktoriálu 3:  
  
     `Factorial 3`  
  
5.  Tento příkaz vytvoří tento výstup: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Další příklady o tom, jak používat argumenty příkazového řádku najdete v tématu [jak: Vytvoření a použití sestavení s pomocí příkazového řádku](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Environment?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
- [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)
