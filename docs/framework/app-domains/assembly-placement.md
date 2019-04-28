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
ms.openlocfilehash: a9b8357be5b9f49569114cbc1c2942eea03696eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675322"
---
# <a name="assembly-placement"></a>Umístění sestavení
Pro většinu aplikací rozhraní .NET Framework můžete vyhledat sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení). Můžete přepsat, kde modul common language runtime vyhledá sestavení s použitím [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Pokud sestavení nemá silný název, umístění zadaného pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresáři aplikace nebo podadresáře. Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) zadat jakékoli umístění v počítači nebo v síti.  
  
 Podobně jako pravidla platí pro vyhledání sestavení, když pracujete s nespravovaným kódem nebo definiční aplikace modelu COM: Pokud sestavení budou sdílet více aplikací, je nutné ji nainstalovat do globální mezipaměti sestavení. Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovnu typů a zaregistrován. Sestavení používá zprostředkovatele komunikace s objekty COM musí být zaregistrovaný v katalogu, i když v některých případech tato registrace probíhá automaticky.  
  
## <a name="see-also"></a>Viz také:

- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)
- [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
