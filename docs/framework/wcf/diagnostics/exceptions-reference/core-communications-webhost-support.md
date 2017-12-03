---
title: "Základní komunikace: Podpora webového hostitele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 707b97c49d6a6f5262719e91f8cb38fe7da53601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-webhost-support"></a>Základní komunikace: Podpora webového hostitele
Toto téma uvádí všechny výjimky generované podpora webového hostitele.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|Hosting_CompatibilityServiceNotHosted|Tato služba vyžaduje režim kompatibility ASP.NET. Musí být také hostované ve službě IIS. Buď hostitele služby IIS s režim kompatibility ASP.NET v souboru Web.config povolena, nebo nastavte vlastnost AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode jiné než požadovanou hodnotu.|  
|Hosting_ListenerNotFoundForActivationInRecycling|Žádný kanál aktivně naslouchá na zadané adrese. Pokud je recyklace aplikace, služby je zavřený.|  
|Hosting_NonHTTPInCompatibilityMode|Pouze protokoly, které jsou podporovány v rámci režim kompatibility ASP.NET jsou HTTP a HTTPS. Odeberte zadaný koncový bod, nebo zakázat režim kompatibility ASP.NET pro aplikaci.|  
|Hosting_ProcessNotExecutingUnderHostedContext|Zadaný hostitelský processcannot být volána v rámci aktuální hostitelské prostředí. Toto rozhraní API vyžaduje, že je volající aplikace hostovat v Internetové informační služby nebo aktivační služba procesů systému Windows.|  
|Hosting_ServiceCompatibilityRequire|Službu nelze aktivovat, protože vyžaduje režim kompatibility ASP.NET. Režim kompatibility ASP.NET není povoleno pro tuto aplikaci. Buď povolte režim kompatibility ASP.NET v souboru Web.config, nebo nastavte AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.|
