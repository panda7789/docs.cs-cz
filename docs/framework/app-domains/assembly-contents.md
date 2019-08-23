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
ms.openlocfilehash: d1334f8c8e1b5898e93697461f609429d4aae764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921706"
---
# <a name="assembly-contents"></a>Obsah sestavení
Obecně platí, že statické sestavení se může skládat ze čtyř prvků:  
  
- [Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md), který obsahuje metadata sestavení.  
  
- Zadejte metadata.  
  
- Kód jazyka MSIL (Microsoft Intermediate Language), který implementuje typy.  
  
- Sada prostředků.  
  
 Vyžaduje se pouze manifest sestavení, ale k sestavení všech smysluplných funkcí je nutné zadat buď typy, nebo prostředky.  
  
 Existuje několik způsobů, jak seskupit tyto prvky do sestavení. Všechny prvky můžete seskupit v jednom fyzickém souboru, který je znázorněn na následujícím obrázku.  
  
 ![Diagram, který zobrazuje sestavení s jedním souborem s názvem MyAssembly. dll.](./media/assembly-contents/single-file-assembly.gif)  
  
 Alternativně mohou být prvky sestavení obsaženy v několika souborech. Tyto soubory mohou být moduly zkompilovaného kódu (.netmodule), prostředky (například soubory .bmp nebo .jpg) nebo jiné soubory vyžadované aplikací. Vytvořte vícesouborové sestavení, pokud chcete kombinovat moduly napsané v různých jazycích a optimalizovat stahování aplikace tím, že zadáte zřídka používané typy v modulu, který se stáhne pouze v případě potřeby.  
  
 Na následujícím obrázku se vývojář hypotetické aplikace rozhodl oddělit některé kódy nástrojů do jiného modulu a uchovávat velký soubor prostředků (v tomto případě obrázek. bmp) v původním souboru. .NET Framework stáhne soubor pouze v případě, že je odkazováno. udržování zřídka odkazovaného kódu v samostatném souboru z aplikace optimalizuje stahování kódu.  
  
 ![Diagram, který zobrazuje vícesouborové sestavení.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
> Soubory, které tvoří vícesouborové sestavení, nejsou fyzicky propojeny systémem souborů. Místo toho jsou propojeny prostřednictvím manifestu sestavení a modul CLR (Common Language Runtime) je spravuje jako celek.  
  
 Na tomto obrázku všechny tři soubory patří do sestavení, jak je popsáno v manifestu sestavení obsaženém v MyAssembly. dll. Do systému souborů jsou tři samostatné soubory. Soubor Util.netmodule byl zkompilován jako modul, protože neobsahuje žádné informace o sestavení. Při vytváření sestavení byl manifest sestavení přidán do knihovny MyAssembly.dll, čímž je naznačen vztah se soubory Util.netmodule a Graphic.bmp.  
  
 Při navrhování zdrojového kódu se při rozhodování o tom, jak rozdělit funkce aplikace do jednoho nebo více souborů, provést explicitní rozhodnutí. Při navrhování .NET Framework kódu provedete podobná rozhodnutí týkající se dělení funkcí do jednoho nebo více sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md)
- [Důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md)
