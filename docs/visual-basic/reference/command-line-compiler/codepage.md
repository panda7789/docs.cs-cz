---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
