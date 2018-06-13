---
title: 'Základní komunikace: Podpora webového hostitele'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 724dc2eb66d058920fda07af899cd7464182c438
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471674"
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
