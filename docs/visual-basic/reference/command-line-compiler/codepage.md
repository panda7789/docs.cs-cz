---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405693"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`id`|Požadováno. Kompilátor používá znakovou stránku určené `id` k interpretaci kódování zdrojové soubory.|  
  
## <a name="remarks"></a>Poznámky  
 Pro kompilaci zdrojového kódu s konkrétním kódováním, můžete použít `-codepage` chcete zadat znakovou stránku, která se má použít. `-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu v kompilaci. Další informace najdete v tématu [kódování znaků v rozhraní .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Možnost není nutná, pokud byly uloženy soubory zdrojového kódu pomocí aktuální znakové stránce ANSI, Unicode nebo UTF-8 s podpisem. Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá, jiné kódování **kódování** dialogové okno. Visual Studio používá **kódování** dialogové okno otevřít soubory zdrojového kódu, které jsou uložené s jinou znakovou stránkou.  
  
> [!NOTE]
>  `-codepage` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
