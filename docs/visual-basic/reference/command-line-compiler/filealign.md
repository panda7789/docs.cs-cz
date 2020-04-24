---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005595"
---
# <a name="-filealign"></a>-filealign
Určuje, kam se mají zarovnat oddíly výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Povinná hodnota. Hodnota, která určuje zarovnání oddílů ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `-filealign` možnosti můžete určit zarovnání oddílů ve výstupním souboru. Oddíly jsou bloky souvislé paměti v přenositelném spustitelném souboru (PE), který obsahuje buď kód, nebo data. `-filealign` Možnost umožňuje zkompilovat aplikaci pomocí nestandardního zarovnání; většinu vývojářů tuto možnost nepotřebují použít.  
  
 Každý oddíl je zarovnán na hranici, která je násobkem `-filealign` hodnoty. Neexistuje žádná pevná výchozí hodnota. Pokud `-filealign` parametr není zadán, kompilátor vybere výchozí hodnotu v době kompilace.  
  
 Zadáním velikosti oddílu můžete změnit velikost výstupního souboru. Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.  
  
> [!NOTE]
> Tato `-filealign` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
