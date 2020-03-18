---
title: Použití průvodce programovacím prostorem My namespace – C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700416"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Použití oboru názvů My (Průvodce programováním jazyka C#)
Obor <xref:Microsoft.VisualBasic.MyServices> názvů`My` (v jazyce Visual Basic) poskytuje snadný a intuitivní přístup k řadě tříd rozhraní .NET Framework, což umožňuje psát kód, který spolupracuje s počítačem, aplikací, nastavením, prostředky a tak dále. Přestože byl původně navržen pro `MyServices` použití s jazykem Visual Basic, obor názvů lze použít v aplikacích jazyka C#.  
  
 Další informace o `MyServices` použití oboru názvů z jazyka Visual Basic naleznete v [tématu Vývoj pomocí aplikace My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Přidání odkazu  
 Před použitím tříd `MyServices` v řešení je nutné přidat odkaz na knihovnu jazyka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Přidání odkazu do knihovny jazyka Visual Basic  
  
1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Odkazy** a vyberte **přidat odkaz**.  
  
2. Po zobrazení dialogového okna **Odkazy** posuňte seznam dolů a vyberte soubor Microsoft.VisualBasic.dll.  
  
     Můžete také zahrnout následující řádek do `using` oddílu na začátku programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá různé statické `MyServices` metody obsažené v oboru názvů. Aby se tento kód zkompiloval, musí být do projektu přidán odkaz na soubor Microsoft.VisualBasic.DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Ne všechny třídy `MyServices` v oboru názvů lze volat z aplikace <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> Jazyka C#: například třída není kompatibilní. V tomto konkrétním případě statické metody, <xref:Microsoft.VisualBasic.FileIO.FileSystem>které jsou součástí , které jsou také obsaženy v souboru VisualBasic.dll, lze použít místo. Zde je například použití jedné takové metody k duplikaci adresáře:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Obory názvů](./index.md)
- [Použití oborů názvů](./using-namespaces.md)
