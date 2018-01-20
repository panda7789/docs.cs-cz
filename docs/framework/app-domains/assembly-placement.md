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
ms.openlocfilehash: 6e52845cad283a643e12deb9c80a1f436840d6bb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="assembly-placement"></a>Umístění sestavení
Pro většinu aplikací rozhraní .NET Framework vyhledejte sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení). Můžete přepsat, kde modul common language runtime vyhledává sestavení pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Pokud sestavení nemá silný název, umístění, pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresář aplikace nebo podadresáři. Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) můžete zadat jakékoli umístění v počítači nebo v síti.  
  
 Podobně jako pravidla použít k vyhledání sestavení při práci s nespravovaným kódem nebo aplikace zprostředkovatele komunikace s objekty COM: Pokud sestavení budou sdílet více aplikací, by měly být nainstalovány do globální mezipaměti sestavení. Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovny typů a zaregistrován. Sestavení používá zprostředkovatel komunikace s objekty COM musí být zaregistrován v katalogu, i když v některých případech se tato registrace probíhá automaticky.  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
