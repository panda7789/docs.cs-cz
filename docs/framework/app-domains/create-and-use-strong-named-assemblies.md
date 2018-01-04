---
title: "Vytváření a používání sestavení se silným názvem"
ms.date: 08/01/2017
ms.prod: .net-framework
ms.technology: dotnet-bcl
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3a087f296a742bc9f0f5672d9bf0cb73c836121
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-and-using-strong-named-assemblies"></a>Vytváření a používání sestavení se silným názvem
<a name="top"></a>Silné jméno se skládá z identity sestavení – jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je zadáno) – plus veřejného klíče a digitální podpis. Generuje se ze souboru sestavení pomocí odpovídajícího privátního klíče. (Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.)  
  
 Sestavení se silným názvem lze použít pouze typy od ostatních sestavení se silným názvem. Jinak by dojít k ohrožení integritu sestavení se silným názvem.  
  
 Tento přehled obsahuje následující části:  
  
-   [Scénář silným názvem](#strong_name_scenario)  
  
-   [Obcházení ověření podpisu důvěryhodných sestavení](#bypassing_signature_verification)  
  
-   [Související témata](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a>Scénář silným názvem  
 Následující scénář popisuje proces podepisování sestavení se silným názvem a později odkazující na s tímto názvem.  
  
1.  Sestavení A je vytvořen se silným názvem pomocí jedné z následujících metod:  
  
    -   Použití vývojového prostředí, které podporuje vytváření silných názvů, například [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
    -   Vytvoření páru kryptografických klíčů pomocí [silný název – nástroj (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) a přiřazení páru klíčů pro sestavení, buď pomocí příkazového řádku kompilátoru nebo [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Windows Software Development Kit (SDK) poskytuje Sn.exe i Al.exe.  
  
2.  Vývojové prostředí nebo nástroj podepisuje hodnota hash souboru, který obsahuje manifest sestavení s privátním klíčem pro vývojáře. Tento digitální podpis je uložen v přenosné spustitelný soubor (PE), který obsahuje manifest sestavení na.  
  
3.  Sestavení B je příjemce sestavení A. Část odkaz na sestavení B manifestu obsahuje token, který představuje sestavení na veřejný klíč. Token je část úplné veřejný klíč a slouží místo klíč sám o sobě ušetřit místo.  
  
4.  Modul CLR ověří podpis silného názvu při umístění sestavení do globální mezipaměti sestavení. Při vytváření vazby silným názvem za běhu, modul CLR porovná klíč uložený v manifestu sestavení B s klíč používaný ke generování silného názvu pro sestavení A. Pokud jsou splněné zabezpečení rozhraní .NET Framework a vazba je úspěšná, sestavení B má jistotu, že s bity sestavení nebylo manipulováno a že tyto bity skutečně pocházejí od vývojářů sestavení A.  
  
> [!NOTE]
>  Tento scénář není vyřešte problémy s vztah důvěryhodnosti. Sestavení mohou obsahovat úplnou podpis Microsoft Authenticode kromě silným názvem. Podpisů Authenticode selhalo zahrnují certifikát, který vytváří vztah důvěryhodnosti. Je důležité si uvědomit, že silné názvy nevyžadují kódu k podpisu tímto způsobem. Silné názvy pouze zadejte jedinečnou identitu.  
  
 [Zpět na začátek](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a>Obcházení ověření podpisu důvěryhodných sestavení  
 Počínaje [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], nedochází k ověřování podpisů silné jméno – když je načten do aplikace plné důvěryhodnosti domény, například výchozí doménu aplikace pro sestavení `MyComputer` zóny. Tento proces se označuje jako silné jméno – Nepoužívat funkce. V prostředí plné důvěryhodnosti jsou požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané, plné důvěryhodnosti sestavení, a to bez ohledu na jejich podpisu. Funkce obejití silného názvu zabraňuje zbytečným režii podpis silného názvu ověření sestavení plné důvěryhodnosti v této situaci umožňuje rychleji načíst sestavení.  
  
 Funkce obcházení vztahuje na všechny sestavení, který je podepsaný se silným názvem, který má následující vlastnosti:  
  
-   Plně důvěryhodný pro bez <xref:System.Security.Policy.StrongName> důkaz (například má `MyComputer` zónu důkaz).  
  
-   Načíst do plně důvěryhodné <xref:System.AppDomain>.  
  
-   Načtené z umístění v rámci <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost této <xref:System.AppDomain>.  
  
-   Podepsáno bez zpoždění.  
  
 Tato funkce lze zakázat pro jednotlivé aplikace nebo pro počítač. V tématu [postupy: Zákaz funkce obejití silného názvu](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Vytvoření páru veřejného a soukromého klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Popisuje postup vytvoření páru kryptografických klíčů pro podepsání sestavení.|  
|[Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Popisuje, jak vytvořit sestavení se silným názvem.|  
|[Vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Popisuje vylepšení silné názvy v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|[Postupy: Odkazování na sestavení se silným názvem](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Popisuje, jak odkazovat typy nebo prostředky v sestavení se silným názvem v době kompilace nebo čas spuštění.|  
|[Postupy: Zákaz funkce obejití silného názvu](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Popisuje, jak zakázat funkci obchází ověřování podpisů silného názvu. Tuto funkci můžete zakázat pro všechny nebo pro konkrétní aplikace.|  
|[Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)|Poskytuje přehled o jeden soubor a vícesouborového sestavení.|  
|[Postup zpoždění podepsání sestavení v sadě Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Vysvětluje, jak pro podepsání sestavení silným názvem, po vytvoření sestavení.|  
|[Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Popisuje nástroje dodávaná v rozhraní .NET Framework, který vám pomůže vytvořit sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.|  
|[Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Popisuje nástroje dodávaná v rozhraní .NET Framework, který generuje soubor, který má manifest z modulů nebo zdrojových souborů sestavení.|
