---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 271606ac021e6afcb28fdac3e1bc86e1aaba7d2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408535"
---
# <a name="-langversion-visual-basic"></a>-langversion – (Visual Basic)
Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena v zadané Visual Basic jazykové verzi.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Argumenty  
 `version`  
 Povinná hodnota. Jazyková verze, která se má použít během kompilace. Přijaté hodnoty jsou `9` , `10` , `11` , `12` , `14` , `15` , `15.3` , `15.5` `default` a `latest` .

 Některá z celých čísel může být zadána také pomocí `.0` jako vedlejší verze, například `11.0` .

 Seznam všech možných hodnot můžete zobrazit zadáním `-langversion:?` příkazu na příkazovém řádku.  
  
## <a name="remarks"></a>Poznámky  
 `-langversion`Možnost určuje, která syntaxe je přijímána kompilátorem. Například pokud určíte, že je jazyková verze 9,0, kompilátor generuje chyby pro syntaxi, která je platná pouze ve verzi 10,0 a novější.  
  
 Tuto možnost můžete použít při vývoji aplikací, které cílí na různé verze .NET Framework. Pokud například cílíte .NET Framework 3,5, můžete použít tuto možnost, abyste se ujistili, že nepoužíváte syntaxi z verze Language 10,0.  
  
 Můžete nastavit `-langversion` přímo jenom pomocí příkazového řádku. Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Příklad  
 Následující kód je zkompilován `sample.vb` pro Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview)
