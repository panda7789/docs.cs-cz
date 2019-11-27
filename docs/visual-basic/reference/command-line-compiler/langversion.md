---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344201"
---
# <a name="-langversion-visual-basic"></a>-langversion – (Visual Basic)
Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena v zadané Visual Basic jazykové verzi.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Argumenty  
 `version`  
 Požadováno. Jazyková verze, která se má použít během kompilace. Přijaté hodnoty jsou `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` a `latest`.

 Některá z celých čísel může být zadána také pomocí `.0` jako dílčí verze, například `11.0`.

 Seznam možných hodnot můžete zobrazit zadáním `-langversion:?` na příkazovém řádku.  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-langversion` určuje, jaká syntaxe je přijímána kompilátorem. Například pokud určíte, že je jazyková verze 9,0, kompilátor generuje chyby pro syntaxi, která je platná pouze ve verzi 10,0 a novější.  
  
 Tuto možnost můžete použít při vývoji aplikací, které cílí na různé verze .NET Framework. Pokud například cílíte .NET Framework 3,5, můžete použít tuto možnost, abyste se ujistili, že nepoužíváte syntaxi z verze Language 10,0.  
  
 `-langversion` lze nastavit přímo pouze pomocí příkazového řádku. Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `sample.vb` pro Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview)
