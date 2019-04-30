---
title: Hostování – výjimky
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934729"
---
# <a name="hosting-exceptions"></a>Hostování – výjimky
Toto téma uvádí všechny výjimky generované Hosting.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Úplný identifikátor URI není povolen. Úplné adresy URI nejsou povoleny pro rozhraní API ServiceHostingEnvironment.EnsureServiceAvailable. Použijte virtuální cestu pro odpovídající službu.|  
|Hosting_BuildProviderCouldNotCreateType|Zadaný typ CLR nelze načíst při kompilaci služby. Ověřte, že tento typ je definován buď ve zdrojovém souboru, který se nachází v aplikačním \\\App_Code adresáři obsažené ve zkompilovaném sestavení nacházejících se v aplikaci prvku \\\bin adresáři nebo v sestavení nainstalovaná v Globální mezipaměti sestavení. Název typu je velká a malá písmena. Adresáře, jako \\\App_Code a \\\bin se musí nacházet v kořenovém adresáři aplikace. \\\App_Code a \\\bin adresáře nemůže být vnořena v podadresářích.|
