---
title: Zápis projektech zacílených na rozhraní .NET Framework 3.0 a 3.5 v sadě Visual Studio 2010
ms.date: 03/30/2017
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
ms.openlocfilehash: 1469ce2906c1101bae4098cbcabd4a10a64c1c7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Zápis projektech zacílených na rozhraní .NET Framework 3.0 a 3.5 v sadě Visual Studio 2010
Můžete použít [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] k vytváření projektů cílených [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze 3.0 nebo 3.5. Toto téma popisuje, jak to provést.  
  
> [!NOTE]
>  Při přidávání aktivity, ujistěte se, že požadované verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nastavena. Změna verze cíle pracovního postupu po přidání aktivity způsobí selhání ověření pracovního postupu.  
  
> [!WARNING]
>  Otevření existující pracovních postupů v [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] mají rozhraní .net Framework 3.5 aktivit dojde k chybě v `this.SetValue()`. Chcete-li otevřít projektů vytvořených v dřívějších verzích rozhraní .net Framework, nejprve otevření prázdné workflow v návrháři a přidejte .net Framework 3.5 aktivity.  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Vytvoření rozhraní .NET Framework 3.0 nebo 3.5 projekt pomocí sady Visual Studio 2010  
  
1.  Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Vyberte **soubor**, **nové**, **projektu**.  
  
3.  V rozevíracím seznamu v horní části dialogových oken, vybrat požadovanou verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>Pro upgrade cílové verze rozhraní .NET Framework  
  
1.  Klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte **vlastnosti**.  
  
2.  V **cílové rozhraní** rozevíracího seznamu vyberte požadovanou verzi.
