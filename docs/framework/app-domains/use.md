---
title: Používání domén aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674884"
---
# <a name="using-application-domains"></a>Používání domén aplikací
Aplikační domény poskytují jednotkovou izolaci pro modul CLR (Common Language Runtime). Jsou vytvořeny a spuštěny uvnitř procesu. Domény aplikace jsou obvykle vytvořeny hostitelem modulu runtime, což je aplikace zodpovědná za načtení modulu runtime do procesu a provádění kódu uživatele v doméně aplikace. Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód uvnitř něj. Mezi hostitele modulu runtime patří ASP.NET, Microsoft Internet Explorer a prostředí systému Windows.  
  
 Pro většinu aplikací nemusíte vytvářet vlastní doménu aplikace. hostitelský modul runtime vytvoří pro vás všechny potřebné aplikační domény. Můžete ale vytvořit a nakonfigurovat další aplikační domény, pokud vaše aplikace potřebuje izolovat kód nebo použít a uvolnit knihovny DLL.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření domény aplikace](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Popisuje, jak programově vytvořit doménu aplikace.  
  
 [Postupy: Uvolnění domény aplikace](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Popisuje způsob, jak programově uvolnit doménu aplikace.  
  
 [Postupy: Konfigurace domény aplikace](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Poskytuje Úvod ke konfiguraci domény aplikace.  
  
 [Načítání informací nastavení z domény aplikace](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Popisuje, jak načíst informace o instalaci z domény aplikace.  
  
 [Postupy: Načtení sestavení do domény aplikace](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Popisuje načtení sestavení do domény aplikace.  
  
 [Postupy: Získání informací o typu a členu ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak načíst informace o sestavení.  
  
 [Stínové kopírování sestavení](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Popisuje, jak stínové kopírování umožňuje aktualizace sestavení, když jsou používány, a jak nakonfigurovat stínové kopírování.  
  
 [Postupy: Přijetí oznámení o první pravděpodobné výjimce](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Vysvětluje, jak můžete obdržet oznámení o vyvolání výjimky před tím, než modul CLR (Common Language Runtime) začne hledat obslužné rutiny výjimek.  
  
 [Řešení načítání sestavení](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Poskytuje pokyny k použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události pro řešení selhání načtení sestavení.  
  
## <a name="reference"></a>Reference  
 <xref:System.AppDomain>  
 Představuje doménu aplikace. Poskytuje metody pro vytváření a řízení domén aplikací.  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje přehled o funkcích, které provádí sestavení.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
 [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Popisuje způsob vytváření dynamických sestavení.  
  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje koncepční přehled domén aplikací.  
  
 [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje způsob použití třídy reflexe k získání informací o sestavení.
