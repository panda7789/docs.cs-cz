---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b065fe488031329815f6ec38da9661fd19700d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529931"
---
# <a name="assembly-location"></a>Umístění sestavení
Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a můžete také určit, zda sestavení lze sdílet s jinými sestaveními. Můžete nasazovat sestavení v následujících umístěních:  
  
-   Adresář nebo podadresáře vaší aplikace.  
  
     Toto je nejběžnější umístění pro nasazení sestavení. Podadresáře kořenový adresář aplikace může být založen na jazyk nebo jazykovou verzi. Pokud sestavení využívá informace v atributu jazykové verze, musí být v podadresáři adresáře aplikace s názvem danou jazykovou verzi.  
  
-   Globální mezipaměti sestavení.  
  
     Toto je mezipaměť kódu celého stroje, který je nainstalován všude, kde je nainstalován modul common language runtime. Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ho do globální mezipaměti sestavení.  
  
-   Na serveru HTTP.  
  
     Nasazení na HTTP server sestavení musí mít silný název; odkazovat na sestavení v části základu kódu konfiguračního souboru aplikace.  
  
## <a name="see-also"></a>Viz také:
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
