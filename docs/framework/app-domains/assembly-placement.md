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
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6669783cf6cac94e8b2335d4b475f1e2b6c5e7e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-placement"></a>Umístění sestavení
Pro většinu aplikací rozhraní .NET Framework vyhledejte sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení). Můžete přepsat, kde modul common language runtime vyhledává sestavení pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Pokud sestavení nemá silný název, umístění, pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresář aplikace nebo podadresáři. Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) můžete zadat jakékoli umístění v počítači nebo v síti.  
  
 Podobně jako pravidla použít k vyhledání sestavení při práci s nespravovaným kódem nebo aplikace zprostředkovatele komunikace s objekty COM: Pokud sestavení budou sdílet více aplikací, by měly být nainstalovány do globální mezipaměti sestavení. Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovny typů a zaregistrován. Sestavení používá zprostředkovatel komunikace s objekty COM musí být zaregistrován v katalogu, i když v některých případech se tato registrace probíhá automaticky.  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
