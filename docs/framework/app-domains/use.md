---
title: Používání domén aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 6ee02a3f27a645f19fd6a327052939586fac4aa9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645426"
---
# <a name="using-application-domains"></a>Používání domén aplikací

Aplikační domény poskytují jednotkovou izolaci pro modul CLR (Common Language Runtime). Jsou vytvořeny a spuštěny uvnitř procesu. Domény aplikace jsou obvykle vytvořeny hostitelem modulu runtime, což je aplikace zodpovědná za načtení modulu runtime do procesu a provádění kódu uživatele v doméně aplikace. Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód uvnitř něj. Mezi hostitele modulu runtime patří ASP.NET, Microsoft Internet Explorer a prostředí systému Windows.  
  
Pro většinu aplikací nemusíte vytvářet vlastní doménu aplikace. hostitelský modul runtime vytvoří pro vás všechny potřebné aplikační domény. Můžete ale vytvořit a nakonfigurovat další aplikační domény, pokud vaše aplikace potřebuje izolovat kód nebo použít a uvolnit knihovny DLL.  
  
## <a name="in-this-section"></a>V tomto oddílu  

[Postupy: Vytvoření domény aplikace](how-to-create-an-application-domain.md)  
Popisuje, jak programově vytvořit doménu aplikace.  
  
[Postupy: Uvolnění domény aplikace](how-to-unload-an-application-domain.md)  
Popisuje způsob, jak programově uvolnit doménu aplikace.  
  
[Postupy: Konfigurace domény aplikace](how-to-configure-an-application-domain.md)  
Poskytuje Úvod ke konfiguraci domény aplikace.  
  
[Načítání informací nastavení z domény aplikace](retrieve-setup-information.md)  
Popisuje, jak načíst informace o instalaci z domény aplikace.  
  
[Postupy: Načtení sestavení do domény aplikace](how-to-load-assemblies-into-an-application-domain.md)  
Popisuje načtení sestavení do domény aplikace.  
  
[Postupy: Získávání informací o typu a členu ze sestavení](../reflection-and-codedom/get-type-member-information.md)  
Popisuje, jak načíst informace o sestavení.  
  
[Stínové kopírování sestavení](shadow-copy-assemblies.md)  
Popisuje, jak stínové kopírování umožňuje aktualizace sestavení, když jsou používány, a jak nakonfigurovat stínové kopírování.  
  
[Postupy: Přijímání oznámení o první odpovídající výjimce](how-to-receive-first-chance-exception-notifications.md)  
Vysvětluje, jak můžete obdržet oznámení o vyvolání výjimky před tím, než modul CLR (Common Language Runtime) začne hledat obslužné rutiny výjimek.  
  
[Řešení načítání sestavení](../../standard/assembly/resolve-loads.md)  
Poskytuje pokyny k použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události pro řešení selhání načtení sestavení.  
  
## <a name="reference"></a>Referenční informace  

<xref:System.AppDomain>  
Představuje doménu aplikace. Poskytuje metody pro vytváření a řízení domén aplikací.  
  
## <a name="related-sections"></a>Související oddíly  
[Sestavení v .NET](../../standard/assembly/index.md)  
Poskytuje přehled o funkcích, které provádí sestavení.  
  
[Programování se sestaveními](../../standard/assembly/index.md)  
Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
[Generování dynamických metod a sestavení](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Popisuje způsob vytváření dynamických sestavení.  
  
[Aplikační domény](application-domains.md)  
Poskytuje koncepční přehled domén aplikací.  
  
[Přehled reflexe](../reflection-and-codedom/reflection.md)  
Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.
