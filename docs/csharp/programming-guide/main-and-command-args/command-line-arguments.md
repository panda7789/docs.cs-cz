---
title: "Argumenty příkazového řádku (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 025ed2c451c0a657ce71db56df603302097fc7ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty příkazového řádku (Průvodce programováním v C#)
Můžete odeslat argumenty, které mají `Main` metoda definováním metodu v jednom z následujících způsobů:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Chcete-li povolit argumenty příkazového řádku v `Main` metoda v aplikaci Windows Forms, je nutné ručně upravit podpis `Main` v souboru program.cs. Vytvoří kód vygenerovaný Návrhář formulářů Windows `Main` bez vstupní parametr. Můžete také použít <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> nebo <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> pro přístup z libovolného bodu na konzole nebo v aplikaci Windows argumenty příkazového řádku.  
  
 Parametr `Main` je metoda <xref:System.String> pole, které představuje argumenty příkazového řádku. Obvykle zjistíte, zda existují argumenty otestováním `Length` vlastnosti, například:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Argumenty řetězce číselnými typy můžete převést také pomocí <xref:System.Convert> třídy nebo `Parse` metoda. Například následující příkaz převede `string` k `long` číslo pomocí <xref:System.Int64.Parse%2A> metoda:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Je také možné použít typ C# `long`, které aliasy `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Můžete také `Convert` třídy metoda `ToInt64` Uděláte to samé:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Další informace naleznete v tématu <xref:System.Int64.Parse%2A> a <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat argumenty příkazového řádku v konzolové aplikaci. Aplikace přijímá jeden argument za běhu, převede argument na celé číslo a vypočítá faktoriál čísla. Pokud jsou zadány žádné argumenty, aplikace vydá zprávu, která vysvětluje správné použití programu.  
  
 Pro zkompilování a spuštění aplikace z příkazového řádku, postupujte takto:  
  
1.  Vložte následující kód do libovolného textového editoru a pak soubor uložte jako textový soubor s názvem `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Z **spustit** obrazovky nebo **spustit** nabídce otevřete Visual Studio **příkazového řádku vývojáře** okno a pak přejděte do složky, která obsahuje soubor, který jste právě vytvořit.  
  
3.  Zadejte následující příkaz pro zkompilování aplikace.  
  
     `csc Factorial.cs`  
  
     Pokud vaše aplikace nemá žádné chyby kompilace. spustitelný soubor, který je pojmenován `Factorial.exe` je vytvořena.  
  
4.  Zadejte následující příkaz, který vypočítat faktoriál 3:  
  
     `Factorial 3`  
  
5.  Příkaz vytvořil tento výstup:`The factorial of 3 is 6.`  
  
> [!NOTE]
>  Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku v [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Další příklady o tom, jak používat argumenty příkazového řádku najdete v tématu [postupy: vytvoření a použití sestavení pomocí příkazu řádek](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Environment?displayProperty=nameWithType>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Main() a argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Postupy: přístup příkazového řádku argumenty pomocí příkazu foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)
