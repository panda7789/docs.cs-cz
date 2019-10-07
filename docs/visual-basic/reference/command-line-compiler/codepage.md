---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002370"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`id`|Požadováno. Kompilátor používá znakovou stránku určenou parametrem `id` pro interpretaci kódování zdrojových souborů.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li zkompilovat zdrojový kód uložený pomocí konkrétního kódování, můžete použít `-codepage` k určení, která znaková stránka má být použita. Možnost `-codepage` se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci. Další informace naleznete v tématu [kódování znaků v .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 Možnost `-codepage` není nutná, pokud byly soubory zdrojového kódu uloženy pomocí aktuální znakové stránky ANSI, Unicode nebo UTF-8 s podpisem. Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá jiné kódování v dialogovém okně **kódování** . Visual Studio používá dialogové okno **kódování** k otevření souborů zdrojového kódu uložených s jinou znakovou stránkou.  
  
> [!NOTE]
> Možnost `-codepage` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
