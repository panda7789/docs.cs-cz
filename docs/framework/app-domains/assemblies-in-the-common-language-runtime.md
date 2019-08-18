---
title: Sestavení v modulu CLR (Common Language Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567358"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Sestavení v modulu CLR (Common Language Runtime)
Sestavení jsou stavební bloky aplikací rozhraní .NET Framework. Tvoří základní jednotku nasazení, správy verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení. Sestavení je kolekce typů a prostředků, které jsou vytvořeny tak, aby vzájemně spolupracovaly a tvořily logickou jednotku funkčnosti. Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace. V modulu runtime neexistuje typ mimo kontext sestavení.  
  
 Sestavení provádí následující funkce:  
  
- Obsahuje kód, který modul CLR (Common Language Runtime) provádí. Kód jazyka MSIL (Microsoft Intermediate Language) v přenositelném spustitelném souboru (PE) nebude spuštěn, pokud mu nebyl přiřazen manifest sestavení. Jednotlivá sestavení mohou mít pouze jeden vstupní bod (tedy `DllMain`, `WinMain` nebo `Main`).  
  
- Vymezuje hranice zabezpečení. Sestavení je jednotka, ve které jsou požadována a udělována oprávnění. Další informace o hranicích zabezpečení při jejich použití pro sestavení naleznete v tématu [požadavky na zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Definuje omezení typu. Jednotlivé identity typu zahrnují název sestavení, ve kterém se nachází. Typ s názvem `MyType`, který je načten v oboru jednoho sestavení, není stejný jako typ s názvem `MyType`, který je načten v oboru jiného sestavení.  
  
- Definuje hranici oboru referencí. Manifest sestavení obsahuje metadata sestavení, která se používají pro překlad typů a která plní požadavky prostředků. Určuje typy a prostředky, které jsou vystaveny mimo sestavení. Manifest také jmenovitě uvádí jiná sestavení, na kterých závisí.  
  
- Definuje omezení verze. Sestavení je nejmenší jednotka schopná správy verzí v modulu CLR (Common Language Runtime). Všechny typy a prostředky ve stejném sestavení jsou označeny stejnou verzí jako celek. Manifest sestavení popisuje závislosti verzí zadané pro všechna závislá sestavení. Další informace o tom, jak se správou verzí, najdete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Vytváří jednotku nasazení. Při spuštění aplikace je nutné, aby byla k dispozici pouze ta sestavení, která aplikace zpočátku volá. Jiná sestavení, jako například prostředky lokalizace nebo sestavení obsahující užitkové třídy, mohou být načtena na požádání. Díky tomu si aplikace při prvním stažení ponechávají malou velikost a jednoduchost. Další informace o nasazení sestavení naleznete v tématu [Deploying Applications](../../../docs/framework/deployment/index.md).  
  
- Je to jednotka, ve které je podporováno souběžné spouštění. Další informace o spuštění více verzí sestavení naleznete v tématu [sestavení a souběžné spouštění](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Sestavení mohou být statická nebo dynamická. Statická sestavení mohou zahrnovat typy rozhraní .NET Framework (rozhraní a třídy) i prostředky pro sestavení (rastrové obrázky, soubory JPEG, soubory prostředků atd.). Statická sestavení jsou uložena na disku v přenosných spustitelných souborech (PE). Rozhraní .NET Framework můžete použít také k vytváření dynamických sestavení, která jsou spouštěna přímo z paměti a před spuštěním nejsou uložena na disk. Na disk můžete dynamická sestavení uložit až poté, co jsou spuštěna.  
  
 Existuje několik způsobů vytváření sestavení. Můžete použít vývojové nástroje, jako je například Visual Studio, které jste v minulosti použili k vytvoření souborů. dll nebo. exe. Pomocí nástrojů, které jsou k dispozici v Windows SDK, můžete vytvářet sestavení s moduly vytvořenými v jiných vývojových prostředích. Můžete také použít rozhraní API modulu CLR (Common Language Runtime <xref:System.Reflection.Emit?displayProperty=nameWithType>), jako je například, k vytvoření dynamického sestavení.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Obsah sestavení](../../../docs/framework/app-domains/assembly-contents.md)|Popisuje prvky, které sestavení vytváří.|  
|[Manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md)|Popisuje data v manifestu sestavení a způsob uložení dat v rámci sestavení.|  
|[Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)|Popisuje globální mezipaměť sestavení (GAC) a způsob jejího používání spolu se sestaveními.|  
|[Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)|Popisuje charakteristiky sestavení se silným názvem.|  
|[Důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md)|Zabývá se funkcí zabezpečení pro sestavení.|  
|[Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)|Poskytuje přehled zásad správy verzí rozhraní .NET Framework.|  
|[Umístění sestavení](../../../docs/framework/app-domains/assembly-placement.md)|Popisuje způsob vyhledání sestavení.|  
|[Sestavení a souběžné spouštění](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Poskytuje přehled o současném použití více verzí modulu runtime nebo sestavení.|  
|[Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)|Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.|  
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Popisuje způsob vytváření dynamických sestavení.|  
|[Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Popisuje způsob, jakým rozhraní .NET Framework překládá odkazy na sestavení v době spuštění.|  
  
## <a name="reference"></a>Reference  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
