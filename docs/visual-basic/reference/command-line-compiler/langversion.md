---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793950"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je zahrnutá v zadané verzi jazyka Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Povinný parametr. Jazykovou verzi používané během kompilace. Platné hodnoty jsou `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` a `latest`.

 Libovolné celé číslo můžete také zadat pomocí `.0` jako vedlejší verze, například `11.0`.

 Zobrazí seznam všech možných hodnot tak, že zadáte `-langversion:?` na příkazovém řádku.  
  
## <a name="remarks"></a>Poznámky  
 `-langversion` Možnost určuje, jaké syntaxe kompilátor přijímá. Například pokud chcete zadat, že je jazyková verze 9.0, kompilátor vygeneruje chyby syntaxe, která je platná pouze ve verzi 10.0 a novější.  
  
 Tuto možnost můžete použít při vývoji aplikací, které jiné cílové verze rozhraní .NET Framework. Například pokud se zaměřujete na rozhraní .NET Framework 3.5, můžete použít tuto možnost k zajištění, že je velmi riskantní používat syntaxi z jazykové verze 10.0.  
  
 Můžete nastavit `-langversion` přímo pouze pomocí příkazového řádku. Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `sample.vb` 9.0 jazyka Visual Basic.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
