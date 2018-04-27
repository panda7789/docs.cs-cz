---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f098dd04b457b7db008788bcfb141af3f69843f8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`id`|Požadováno. Kompilátor používá znaková stránka určeného `id` interpretovat kódování zdrojové soubory.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilace zdrojového kódu uložit s konkrétním kódování, můžete použít `-codepage` k zadat znakovou stránku, která má být použita. `-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu v kompilaci. Další informace najdete v tématu [kódování znaků v rozhraní .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Možnost není nutný v případě, že soubory zdrojového kódu se uložily pomocí aktuální znaková stránka ANSI, Unicode nebo UTF-8 podpisem. Visual Studio uloží všechny soubory zdrojového kódu s aktuální znaková stránka ANSI ve výchozím nastavení, pokud uživatel zadá jiné kódování v **kódování** dialogové okno. Visual Studio použije **kódování** dialogové okno otevřít soubory zdrojového kódu, které jsou uložené s jinou kódovou stránku.  
  
> [!NOTE]
>  `-codepage` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
