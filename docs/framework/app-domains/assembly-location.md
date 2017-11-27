---
title: "Umístění sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e069c1636004896bfb193fd70a352195ba045865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-location"></a>Umístění sestavení
Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a také dokáže určit, zda je sestavení je možné sdílet s ostatních sestavení. Můžete nasadit sestavení v následujících umístěních:  
  
-   Adresář nebo podadresáře aplikace.  
  
     Toto je nejběžnější umístění pro nasazení sestavení. Podadresáře kořenovému adresáři aplikace může být založen na jazyk nebo jazykovou verzi. Pokud má sestavení informace v atributu jazykovou verzi, musí být v podadresáři v adresáři aplikace s názvem tuto jazykovou verzi.  
  
-   Globální mezipaměti sestavení.  
  
     Jde o mezipaměť strojový kód, který je nainstalován, kde je nainstalován modul common language runtime. Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ji do globální mezipaměti sestavení.  
  
-   Na serveru HTTP.  
  
     Sestavení nasazeno na HTTP serveru musí mít silný název; Nasměrujte sestavení v sekci codebase konfiguračního souboru aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
