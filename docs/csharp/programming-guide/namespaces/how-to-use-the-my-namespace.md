---
title: "Postupy: Použití oboru názvů My (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3564c594a5fbb9bd05a956e5c12bbb173d2db51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Postupy: Použití oboru názvů My (Průvodce programováním v C#)
<xref:Microsoft.VisualBasic.MyServices> Obor názvů (`My` v jazyce Visual Basic) poskytuje snadný a intuitivní přístup k několik tříd rozhraní .NET Framework, což umožňuje psát kód, který komunikuje s počítači, aplikace, nastavení, prostředky a tak dále. Přestože původně navržený pro použití v jazyce Visual Basic `MyServices` obor názvů mohou být používány aplikací v C#.  
  
 Další informace o používání `MyServices` oboru názvů z jazyka Visual Basic, najdete v části [vývoj s Moje](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Přidání odkazu na  
 Než budete moci použít `MyServices` třídy ve vašem řešení, musíte přidat odkaz na knihovnu jazyka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Chcete-li přidat odkaz na knihovnu jazyka Visual Basic  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz na**.  
  
2.  Když **odkazy** se zobrazí dialogové okno, přejděte dolů v seznamu a vyberte souboru Microsoft.VisualBasic.dll.  
  
     Můžete také obsahuje následující řádek v `using` části při spuštění aplikace.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Příklad  
 Volá různých statických metod, které jsou obsažené v tomto příkladu `MyServices` oboru názvů. Pro tento kód mohl zkompilovat musí být odkaz na souboru Microsoft.VisualBasic.DLL přidat do projektu.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Ne všechny třídy v `MyServices` oboru názvů lze volat z aplikace v jazyce C#: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní. V tomto konkrétním případě statických metod které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem>, které jsou také obsaženy v VisualBasic.dll, může být místo toho použít. Zde je například jak duplicitní adresáře pomocí jedna z těchto metod:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
 [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)
