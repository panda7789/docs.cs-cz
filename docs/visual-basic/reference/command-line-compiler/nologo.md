---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335438"
---
# <a name="-nologo-visual-basic"></a>-unlogo (Visual Basic)
Potlačí zobrazení nápisu copyrightu a informativní zprávy během kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte `-nologo`, kompilátor nezobrazí banner s copyrightem. Ve výchozím nastavení `-nologo` neplatí.  
  
> [!NOTE]
> Možnost `-nologo` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a nezobrazuje banner s copyrightem.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
