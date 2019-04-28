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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674884"
---
# <a name="using-application-domains"></a>Používání domén aplikací
Aplikační domény poskytují jednotka izolace pro modul common language runtime. Jsou vytvořeny a spuštění uvnitř procesu. Aplikační domény jsou obvykle vytvořeny od hostitele runtime, který je zodpovědný za načítání modulu runtime do procesu a provádění uživatelského kódu v rámci domény aplikace aplikace. Hostitelský modul runtime vytvoří proces a výchozí domény aplikace a spouští spravovaný kód uvnitř. Hostitelská prostředí modulu runtime zahrnují technologie ASP.NET, Microsoft Internet Explorer a prostředí Windows.  
  
 Pro většinu aplikací nepotřebujete k vytvoření vlastní domény aplikace. hostitelský modul runtime vytvoří všechny nezbytné domény aplikace. Můžete však vytvořit a nakonfigurovat další domény aplikace, pokud vaše aplikace potřebuje k izolaci kódu nebo použití a uvolnění knihoven DLL.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření domény aplikace](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Popisuje, jak prostřednictvím kódu programu vytvořit doménu aplikace.  
  
 [Postupy: Uvolnění domény aplikace](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Popisuje, jak prostřednictvím kódu programu uvolnění domény aplikace.  
  
 [Postupy: Konfigurace domény aplikace](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Poskytuje úvod do konfigurace domény aplikace.  
  
 [Načítání informací nastavení z domény aplikace](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Popisuje, jak načíst informace o nastavení z domény aplikace.  
  
 [Postupy: Načtení sestavení do domény aplikace](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Popisuje, jak načíst sestavení do domény aplikace.  
  
 [Postupy: Získávání informací o člen typu a ze sestavení](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Popisuje, jak načíst informace o sestavení.  
  
 [Stínové kopírování sestavení](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Popisuje, jak stínové kopírování sestavení umožňuje instalaci aktualizací do sestavení za použití a jak konfigurovat stínové kopírování sestavení.  
  
 [Postupy: Přijímání oznámení o první odpovídající výjimce](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Vysvětluje, jak můžete dostávat oznámení, že byla vyvolána výjimka, než začne hledat obslužné rutiny výjimek common language runtime.  
  
 [Řešení načítání sestavení](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Obsahuje informace o použití <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí k vyřešení selhání při načítání sestavení.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.AppDomain>  
 Představuje doménu aplikace. Poskytuje metody pro vytváření a řízení aplikačních doménách.  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Obsahuje přehled funkce prováděné sestavení.  
  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Popisuje způsob vytváření, podepisování a nastavení atributů v rámci sestavení.  
  
 [Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Popisuje způsob vytváření dynamických sestavení.  
  
 [Aplikační domény](../../../docs/framework/app-domains/application-domains.md)  
 Poskytuje koncepční přehled domén aplikací.  
  
 [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.
