---
title: Umístění sestavení
description: Přečtěte si pokyny pro umístění sestavení .NET v adresářích (například v globální mezipaměti sestavení nebo v adresáři nebo v adresáři aplikace).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104961"
---
# <a name="assembly-placement"></a>Umístění sestavení
Pro většinu .NET Frameworkch aplikací naleznete sestavení, která tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sestavení sdíleno). Můžete přepsat, kde modul CLR (Common Language Runtime) hledá sestavení pomocí [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Pokud sestavení nemá silný název, umístění zadané pomocí [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) je omezeno na adresář aplikace nebo na podadresář. Pokud má sestavení silný název, [ \<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md) může určovat libovolné umístění v počítači nebo v síti.  
  
 Podobná pravidla se vztahují na lokalizaci sestavení při práci s nespravovaným kódem nebo aplikacemi COM interop: Pokud bude sestavení sdíleno více aplikacemi, měla by být nainstalována do globální mezipaměti sestavení (GAC). Sestavení použitá s nespravovaným kódem musí být exportována jako knihovna typů a zaregistrována. Sestavení používaná zprostředkovatelem komunikace s objekty COM musí být registrována v katalogu, i když v některých případech tato registrace probíhá automaticky.  
  
## <a name="see-also"></a>Viz také

- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurace aplikací](../configure-apps/index.md)
- [Spolupráce s nespravovaným kódem](../interop/index.md)
- [Sestavení v .NET](index.md)
