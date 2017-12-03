---
title: "Hostování – výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfbe5fa9944b97704f153e9b38229ddfd28a9c5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-exceptions"></a>Hostování – výjimky
Toto téma uvádí všechny výjimky generované Hosting.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Úplný identifikátor URI není povolen. Úplné identifikátory URI nejsou povoleny pro rozhraní API třídy ServiceHostingEnvironment.EnsureServiceAvailable. Použijte virtuální cestu pro příslušné služby.|  
|Hosting_BuildProviderCouldNotCreateType|Zadaný typ CLR nelze načíst během kompilace služby. Ověřte, že tento typ je definována buď v zdrojový soubor nachází v aplikačním \\directory \App_Code, obsažené v kompilovaném sestavení umístěném v aplikačním \\\bin adresář, nebo existuje v sestavení nainstalovaném v Globální mezipaměť sestavení. Název typu rozlišuje velká a malá písmena. Adresářů, jako \\\App_Code a \\\bin se musí nacházet v kořenovém adresáři aplikace. \\\App_Code a \\\bin adresáře nemůže být vnořena nacházejí v podadresářích adresáře.|
