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
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929475"
---
# <a name="-filealign"></a>-filealign
Určuje, kam se mají zarovnat oddíly výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Povinný parametr. Hodnota, která určuje zarovnání oddílů ve výstupním souboru. Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192. Tyto hodnoty jsou v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `-filealign` možnosti můžete určit zarovnání oddílů ve výstupním souboru. Oddíly jsou bloky souvislé paměti v přenositelném spustitelném souboru (PE), který obsahuje buď kód, nebo data. `-filealign` Možnost umožňuje zkompilovat aplikaci pomocí nestandardního zarovnání; většina vývojářů tuto možnost nepotřebuje.  
  
 Každý oddíl je zarovnán na hranici, která je násobkem `-filealign` hodnoty. Neexistuje žádná pevná výchozí hodnota. Pokud `-filealign` parametr není zadán, kompilátor vybere výchozí hodnotu v době kompilace.  
  
 Zadáním velikosti oddílu můžete změnit velikost výstupního souboru. Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.  
  
> [!NOTE]
> Tato `-filealign` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
