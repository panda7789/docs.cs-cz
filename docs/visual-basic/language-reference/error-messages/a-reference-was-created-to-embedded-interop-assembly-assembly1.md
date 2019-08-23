---
title: Byl vytvořen odkaz na vložené definiční sestavení '<assembly1>' z důvodu nepřímého odkazu na toto sestavení ze sestavení '<assembly2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 0f7a136abb0e63e4b139b87c8f18ae3fcb99dbf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947750"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>Byl vytvořen odkaz na vložené definiční sestavení\<assembly1 > z důvodu nepřímého odkazu na toto sestavení ze\<sestavení Assembly2 >.
Byl vytvořen odkaz na vložené sestavení vzájemné spolupráce '\<assembly1 > ' z důvodu nepřímého odkazu na toto sestavení ze sestavení\<' Assembly2 > '. Zvažte změnu vlastnosti "Embed Interop Types" v obou sestaveních.  
  
 Přidali jste odkaz na sestavení (assembly1), které má `Embed Interop Types` vlastnost nastavenou na. `True` Tento příkaz instruuje kompilátor, aby do tohoto sestavení vložil informace o typu spolupráce. Kompilátor však nemůže vložit informace o typu spolupráce z tohoto sestavení, protože jiné sestavení, na které jste odkazován (Assembly2), také odkazuje na toto sestavení (assembly1) `Embed Interop Types` a má vlastnost `False`nastavenu na hodnotu.  
  
> [!NOTE]
> Nastavení vlastnosti na `True` odkaz na sestavení je ekvivalentní k odkazování na sestavení pomocí `/link` možnosti pro kompilátor příkazového řádku. `Embed Interop Types`  
  
 **ID chyby:** BC40059  
  
### <a name="to-address-this-warning"></a>Řešení tohoto upozornění  
  
- Pro vložení informací o typu spolupráce pro obě sestavení nastavte `Embed Interop Types` vlastnost na všech odkazech na assembly1 na. `True`  
  
- Chcete-li odstranit upozornění, můžete nastavit `Embed Interop Types` vlastnost assembly1 na `False`hodnotu. V tomto případě jsou informace o typu spolupráce poskytovány pomocí primárního definičního sestavení (PIA).  
  
## <a name="see-also"></a>Viz také:

- [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
