---
title: 'Postupy: Použití průvodce C# programováním v mém oboru názvů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ff00a60d92ec6abbeb257abec76ed2812867f651
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588873"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Postupy: Použití oboru názvů My (C# Průvodce programováním)
Obor názvů (`My` v Visual Basic) poskytuje snadný a intuitivní přístup k řadě .NET Framework tříd, což vám umožní napsat kód, který komunikuje s počítačem, aplikací, nastavením, prostředky a tak dále. <xref:Microsoft.VisualBasic.MyServices> I když je `MyServices` původně určený pro použití s Visual Basic, obor názvů se dá C# použít v aplikacích.  
  
 Další informace o používání `MyServices` oboru názvů z Visual Basic naleznete v tématu [vývoj s My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Přidání odkazu  
 Než budete moci použít `MyServices` třídy ve vašem řešení, je nutné přidat odkaz na knihovnu Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Přidání odkazu do knihovny Visual Basic  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.  
  
2. Když se zobrazí dialogové okno **odkazy** , přejděte dolů na seznam a vyberte Microsoft. VisualBasic. dll.  
  
     V `using` části na začátku programu můžete také chtít zahrnout následující řádek.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá různé statické metody obsažené v `MyServices` oboru názvů. Pro zkompilování tohoto kódu musí být do projektu přidán odkaz na Microsoft. VisualBasic. DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Ne všechny třídy v `MyServices` oboru názvů mohou být volány z C# aplikace: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní. V tomto konkrétním případě lze místo toho použít statické metody, které <xref:Microsoft.VisualBasic.FileIO.FileSystem>jsou součástí, které jsou také obsaženy v souboru VisualBasic. dll. Tady je příklad, jak použít jednu takovou metodu pro duplikaci adresáře:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Obory názvů](./index.md)
- [Použití oboru názvů](./using-namespaces.md)
