---
title: Jak používat můj obor názvů – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700416"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Použití oboru názvů My (C# Průvodce programováním)
Obor názvů <xref:Microsoft.VisualBasic.MyServices> (`My` v Visual Basic) poskytuje snadný a intuitivní přístup k řadě tříd .NET Framework a umožňuje psát kód, který komunikuje s počítačem, aplikací, nastavením, prostředky a tak dále. I když je původně určený pro použití s Visual Basic, `MyServices` obor názvů se dá C# použít v aplikacích.  
  
 Další informace o použití `MyServices` oboru názvů z Visual Basic naleznete v tématu [vývoj s My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Přidání odkazu  
 Než budete moci použít třídy `MyServices` ve vašem řešení, je nutné přidat odkaz na knihovnu Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Přidání odkazu do knihovny Visual Basic  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.  
  
2. Když se zobrazí dialogové okno **odkazy** , přejděte dolů na seznam a vyberte Microsoft. VisualBasic. dll.  
  
     Můžete také zahrnout následující řádek do části `using` na začátku programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá různé statické metody obsažené v oboru názvů `MyServices`. Pro zkompilování tohoto kódu musí být do projektu přidán odkaz na Microsoft. VisualBasic. DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Ne všechny třídy v oboru názvů `MyServices` mohou být volány z C# aplikace: například třída <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> není kompatibilní. V tomto konkrétním případě lze místo toho použít statické metody, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem>, které jsou také obsaženy v souboru VisualBasic. dll. Tady je příklad, jak použít jednu takovou metodu pro duplikaci adresáře:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Obory názvů](./index.md)
- [Použití oboru názvů](./using-namespaces.md)
