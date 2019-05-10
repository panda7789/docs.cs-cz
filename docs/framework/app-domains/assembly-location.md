---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c736b4fe2a4bc38d4345413fa00d4cf7e5a80be7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607723"
---
# <a name="assembly-location"></a>Umístění sestavení
Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a můžete také určit, zda sestavení lze sdílet s jinými sestaveními. Můžete nasazovat sestavení v následujících umístěních:  
  
- Adresář nebo podadresáře vaší aplikace.  
  
     Toto je nejběžnější umístění pro nasazení sestavení. Podadresáře kořenový adresář aplikace může být založen na jazyk nebo jazykovou verzi. Pokud sestavení využívá informace v atributu jazykové verze, musí být v podadresáři adresáře aplikace s názvem danou jazykovou verzi.  
  
- Globální mezipaměti sestavení.  
  
     Toto je mezipaměť kódu celého stroje, který je nainstalován všude, kde je nainstalován modul common language runtime. Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ho do globální mezipaměti sestavení.  
  
- Na serveru HTTP.  
  
     Nasazení na HTTP server sestavení musí mít silný název; odkazovat na sestavení v části základu kódu konfiguračního souboru aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
