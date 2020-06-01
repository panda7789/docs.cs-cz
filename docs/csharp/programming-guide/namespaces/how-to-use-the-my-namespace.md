---
title: Jak používat můj obor názvů – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241939"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Jak používat můj obor názvů (Průvodce programováním v C#)

<xref:Microsoft.VisualBasic.MyServices>Obor názvů ( `My` v Visual Basic) poskytuje snadný a intuitivní přístup k několika třídám .NET a umožňuje psát kód, který komunikuje s počítačem, aplikací, nastavením, prostředky a tak dále. I když je původně určený pro použití s Visual Basic, `MyServices` obor názvů lze použít v aplikacích C#.  
  
 Další informace o používání `MyServices` oboru názvů z Visual Basic naleznete v tématu [vývoj s My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="add-a-reference"></a>Přidat odkaz

 Než budete moci použít `MyServices` třídy ve vašem řešení, je nutné přidat odkaz na knihovnu Visual Basic.  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a>Přidat odkaz na knihovnu Visual Basic  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.  
  
2. Když se zobrazí dialogové okno **odkazy** , přejděte dolů na seznam a vyberte Microsoft. VisualBasic. dll.  
  
     V části na začátku programu můžete také chtít zahrnout následující řádek `using` .  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá různé statické metody obsažené v `MyServices` oboru názvů. Pro zkompilování tohoto kódu musí být do projektu přidán odkaz na Microsoft. VisualBasic. DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Ne všechny třídy v `MyServices` oboru názvů mohou být volány z aplikace jazyka C#: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní. V tomto konkrétním případě lze místo toho použít statické metody, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem> , které jsou také obsaženy v souboru VisualBasic. dll. Tady je příklad, jak použít jednu takovou metodu pro duplikaci adresáře:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Obory názvů](./index.md)
- [Používání oborů názvů](./using-namespaces.md)
