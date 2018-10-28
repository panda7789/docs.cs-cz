---
title: Obsah sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aed7e1e9e85f746c4b55b10c59dd82e85565b00
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194836"
---
# <a name="assembly-contents"></a>Obsah sestavení
Obecně platí Statická sestavení se může skládat z čtyři elementy:  
  
-   [Manifestu sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.  
  
-   Typ metadat.  
  
-   Microsoft intermediate language (MSIL) kód, který implementuje typy.  
  
-   Sada prostředků.  
  
 Vyžaduje se jenom manifest sestavení, ale typy nebo prostředky je nutné poskytnout sestavení žádné smysluplné funkce.  
  
 Existuje několik způsobů seskupení těchto prvků v sestavení. Můžete seskupit všechny prvky v jednom fyzickém souboru, která je znázorněna na následujícím obrázku.  
  
 ![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")  
Jeden soubor sestavení  
  
 Alternativně prvky sestavení mohou být obsaženy v několika souborů. Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací. Pokud chcete kombinovat modulů napsaných v různých jazycích tak, že aplikace tak, že vložíte zřídka použít typy v modulu, který se stáhne jenom v případě potřeby vytvořte vícesouborové sestavení.  
  
 Na následujícím obrázku vývojář aplikace hypotetické zvolil oddělit nějaký kód nástroje do jiného modulu a zachovat velkého souboru prostředků (v tomto případě obrázek bmp) v původním souboru. Rozhraní .NET Framework stáhne soubor pouze v případě, že se na ni odkazuje; udržování kódu zřídka odkazované v samostatném souboru z aplikace optimalizuje kód ke stažení.  
  
 ![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")  
Vícesouborová sestavení  
  
> [!NOTE]
>  Soubory, které tvoří vícesouborového sestavení nejsou fyzicky připojeny systémem souborů. Místo toho jsou propojeny prostřednictvím manifest sestavení a modul common language runtime spravuje jako celek.  
  
 Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení součástí MyAssembly.dll. Jsou tři samostatné soubory do systému souborů. Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení. Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.  
  
 Při návrhu aktuálně zdrojového kódu, proveďte explicitní rozhodnutí o tom, jak rozdělit funkce vaší aplikace do jednoho nebo více souborů. Při navrhování kódu rozhraní .NET Framework, bude podobné rozhodnutí o tom, jak rozdělit funkce do jednoho nebo více sestavení.  
  
## <a name="see-also"></a>Viz také  
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md)  
- [Důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md)
