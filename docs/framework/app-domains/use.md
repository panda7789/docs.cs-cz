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
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="using-application-domains"></a>Používání domén aplikací
Aplikační domény zadejte jednotku pro izolaci pro modul common language runtime. Jsou vytvořeny a spustit uvnitř proces. Aplikační domény jsou obvykle vytvořené pomocí modulu runtime hostitele, který je zodpovědný za načítání modulu runtime do procesu a spuštění uživatelského kódu v rámci domény aplikace aplikace. Hostitel modulu runtime vytvoří proces a výchozí doménu aplikace a spustí spravovaný kód je uvnitř. Modulu runtime zahrnout ASP.NET, aplikace Microsoft Internet Explorer a prostředí systému Windows.  
  
 Pro většinu aplikací není nutné k vytvoření vlastní domény aplikace. hostitel modulu runtime pro vás vytvoří všechny nezbytné domény aplikace. Můžete však vytvořit a nakonfigurovat další domény aplikace, pokud aplikace potřebuje izolovat kódu nebo použití a uvolnění knihovny DLL.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření domény aplikace](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Popisuje postup vytváření domény aplikace prostřednictvím kódu programu.  
  
 [Postupy: Uvolnění domény aplikace](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Popisuje, jak programově uvolnění domény aplikace.  
  
 [Postupy: Konfigurace domény aplikace](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Poskytuje úvod do konfigurace domény aplikace.  
  
 [Načítání informací nastavení z domény aplikace](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Popisuje, jak načíst informace o instalaci z domény aplikace.  
  
 [Postupy: Načtení sestavení do domény aplikace](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Popisuje, jak načíst sestavení do domény aplikace.  
  
 [Postupy: Získávání informací o typu a členu ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak načíst informace o sestavení.  
  
 [Stínové kopírování sestavení](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Popisuje, jak stínové kopírování umožňuje aktualizace sestavení při se používají a postup konfigurace stínové kopírování sestavení.  
  
 [Postupy: Přijímání oznámení o první odpovídající výjimce](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Vysvětluje, jak může přijímat oznámení, že byla vyvolána výjimka, než začne modul common language runtime hledat obslužné rutiny výjimek.  
  
 [Řešení načítání sestavení](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Obsahuje informace o použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí k vyřešení selhání načtení sestavení.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.AppDomain>  
 Představuje domény aplikace. Poskytuje metody pro vytváření a řízení aplikační domény.  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Obsahuje přehled funkce provádí sestavení.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
 [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Popisuje způsob vytváření dynamických sestavení.  
  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje koncepční přehled domén aplikací.  
  
 [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje postup použití **reflexe** třída získat informace o sestavení.
