---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: a38fb4be9347b3372b4a459fce2e96b9e38c3a51
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343549"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`id`|Povinná hodnota. Kompilátor používá znakovou stránku určenou nástrojem `id` k interpretaci kódování zdrojových souborů.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li zkompilovat zdrojový kód uložený pomocí konkrétního kódování, `-codepage` můžete použít k určení, která znaková stránka má být použita. `-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci. Další informace naleznete v tématu [kódování znaků v .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 `-codepage` Možnost není nutná, pokud byly soubory zdrojového kódu uloženy pomocí aktuální znakové stránky ANSI, Unicode nebo UTF-8 s podpisem. Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá jiné kódování v dialogovém okně **kódování** . Visual Studio používá dialogové okno **kódování** k otevření souborů zdrojového kódu uložených s jinou znakovou stránkou.  
  
> [!NOTE]
> Tato `-codepage` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
