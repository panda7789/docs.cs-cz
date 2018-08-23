---
title: 'Základní komunikace: Podpora webového hostitele'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752313"
---
# <a name="core-communications-webhost-support"></a>Základní komunikace: Podpora webového hostitele

Toto téma uvádí všechny výjimky generované podpora webového hostitele.

## <a name="exception-list"></a>Seznam výjimek

|Kód zdroje|Řetězec prostředku|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|Tato služba vyžaduje režim kompatibility ASP.NET. Musí být také hostovány ve službě IIS. Buď hostovat službu ve službě IIS pomocí režim kompatibility ASP.NET zapnutou v souboru Web.config nebo nastavte vlastnost AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode jinou hodnotu než Required.|
|Hosting_ListenerNotFoundForActivationInRecycling|Žádný kanál aktivně naslouchá na zadané adrese. Pokud aplikace se recykluje, ukončení služby.|
|Hosting_NonHTTPInCompatibilityMode|Pouze protokoly, které jsou podporovány v rámci režim kompatibility ASP.NET jsou HTTP a HTTPS. Odeberte zadaný koncový bod nebo zakažte režim kompatibility ASP.NET pro aplikaci.|
|Hosting_ProcessNotExecutingUnderHostedContext|Zadaný hostitelský proces nelze vyvolat v aktuálním prostředí hostování. Toto rozhraní API vyžaduje, aby volající aplikace byla hostována v Internetové informační službě nebo služba Windows Process Activation Service.|
|Hosting_ServiceCompatibilityRequire|Službu nelze aktivovat, protože vyžaduje režim kompatibility ASP.NET. Režim kompatibility ASP.NET není povolena pro tuto aplikaci. Povolte režim kompatibility ASP.NET v souboru Web.config nebo nastavte AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.|
