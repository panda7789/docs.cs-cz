---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d42b73d1ec20e66d604f19bb836cb7e2778e62f0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505986"
---
# <a name="assembly-placement"></a>Umístění sestavení
Pro většinu aplikací rozhraní .NET Framework můžete vyhledat sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení). Můžete přepsat, kde modul common language runtime vyhledá sestavení s použitím [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Pokud sestavení nemá silný název, umístění zadaného pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresáři aplikace nebo podadresáře. Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) zadat jakékoli umístění v počítači nebo v síti.  
  
 Podobně jako pravidla platí pro vyhledání sestavení, když pracujete s nespravovaným kódem nebo definiční aplikace modelu COM: Pokud sestavení budou sdílet více aplikací, je nutné ji nainstalovat do globální mezipaměti sestavení. Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovnu typů a zaregistrován. Sestavení používá zprostředkovatele komunikace s objekty COM musí být zaregistrovaný v katalogu, i když v některých případech tato registrace probíhá automaticky.  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Rozšířená interoperabilita modelu COM](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
