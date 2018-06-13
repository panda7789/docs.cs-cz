---
title: Hostování – výjimky
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469434"
---
# <a name="hosting-exceptions"></a>Hostování – výjimky
Toto téma uvádí všechny výjimky generované Hosting.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Úplný identifikátor URI není povolen. Úplné identifikátory URI nejsou povoleny pro rozhraní API třídy ServiceHostingEnvironment.EnsureServiceAvailable. Použijte virtuální cestu pro příslušné služby.|  
|Hosting_BuildProviderCouldNotCreateType|Zadaný typ CLR nelze načíst během kompilace služby. Ověřte, že tento typ je definována buď v zdrojový soubor nachází v aplikačním \\directory \App_Code, obsažené v kompilovaném sestavení umístěném v aplikačním \\\bin adresář, nebo existuje v sestavení nainstalovaném v Globální mezipaměť sestavení. Název typu rozlišuje velká a malá písmena. Adresářů, jako \\\App_Code a \\\bin se musí nacházet v kořenovém adresáři aplikace. \\\App_Code a \\\bin adresáře nemůže být vnořena nacházejí v podadresářích adresáře.|
