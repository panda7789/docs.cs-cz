---
title: "Nastavování atributů sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f95d8c5f78dfa9ec388cfa63b81857ffe580abf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="setting-assembly-attributes"></a>Nastavování atributů sestavení
Atributů sestavení jsou hodnoty, které obsahují informace o sestavení. Atributy jsou rozdělené do následujících skupin informací:  
  
-   Atributy identity sestavení.  
  
-   Informační atributy.  
  
-   Atributy manifestu sestavení.  
  
-   Silné jméno atributy.  
  
## <a name="assembly-identity-attributes"></a>Atributy Identity sestavení  
 Tři atributy společně se silným názvem (pokud existuje), zjistit identitu sestavení: název, verzi a jazykovou verzi. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování na sestavení v kódu. Atributy slouží k nastavení verze sestavení a jazykové verze. Kompilátor nebo [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) nastaví hodnotu názvu při vytváření sestavení, založené na souboru, který obsahuje manifest sestavení.  
  
 Následující tabulka popisuje atributy verze a jazykové verze.  
  
|Atribut identity sestavení|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Položka výčtu označující jazykovou verzi, která podporuje sestavení. Sestavení může také nezávislé na jazykové verzi, která udává, že obsahuje prostředky pro výchozí jazykovou verzi. **Poznámka:** modulu runtime zpracovává všechny sestavení, které nemá atribut jazykové verze nastavte na hodnotu null, jako je satelitní sestavení. Takové sestavení podléhají satelitní sestavení vazbu pravidla. Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Hodnota, která nastaví sestavení atributy, jako je například jestli sestavení lze spustit souběžně.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Číselnou hodnotu ve formátu *hlavní*. *méně závažné*. *sestavení*. *Revize* (například 2.4.0.0). Modul CLR používá tato hodnota k provedení vazby operací v sestavení se silným názvem. **Poznámka:** Pokud <xref:System.Reflection.AssemblyInformationalVersionAttribute> atribut není použit k sestavení číslo verze zadané parametrem <xref:System.Reflection.AssemblyVersionAttribute> atribut je používán <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, a <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> vlastnosti.|  
  
 Následující příklad kódu ukazuje, jak se má použít k sestavení atributy verze a jazykovou verzi.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Informační atributy  
 Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení. Následující tabulka popisuje informační atributy, které můžete použít k sestavení.  
  
|Informační atribut|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Řetězcová hodnota určující název společnosti.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Řetězec hodnota, která určuje informace o autorských právech.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Řetězcová hodnota zadání čísla verze souboru Win32. To obvykle výchozí verze sestavení.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Řetězec hodnota, která určuje informace o verzi, kterou nepoužívá modul common language runtime, jako je například číslo verze plnou verzi produktu. **Poznámka:** Pokud tento atribut se používá k sestavení, určující řetězec lze získat v době běhu pomocí <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> vlastnost. Řetězec se používá také v cestě a registru klíči poskytované <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> vlastnosti.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Řetězec hodnota, která určuje informace o produktu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Řetězec hodnota, která určuje informace o ochranných známkách.|  
  
 Tyto atributy lze zobrazit na stránce vlastností sestavení nebo je můžete přepsat pomocí **/win32res** – možnost kompilátoru k určení vlastního souboru Win32 prostředků.  
  
## <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení  
 Atributy manifestu sestavení můžete použít k poskytování informací v manifestu sestavení, včetně názvu, popisu, výchozí alias a konfigurace. Následující tabulka popisuje atributy manifestu sestavení.  
  
|Atribut manifestu sestavení|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Řetězec hodnotu, která určuje konfiguraci sestavení, např. prodejní nebo verze pro ladění. Modul runtime tuto hodnotu nepoužívá.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Řetězcová hodnota určující výchozí alias, který se má použít při odkazování na sestavení. Tuto hodnotu poskytuje popisný název, pokud není název sestavení, samotné popisný (například hodnota identifikátoru GUID). Tuto hodnotu můžete použít také jako krátkou verzi úplného názvu sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Řetězcová hodnota zadání krátký popis, který shrnuje povahu a účel sestavení.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Řetězcová hodnota zadat popisný název sestavení. Sestavení s názvem comdlg například může mít název Microsoft běžného ovládacího prvku dialogové okno.|  
  
## <a name="strong-name-attributes"></a>Atributy silného názvu  
 Silné jméno atributy slouží k nastavení silný název sestavení. Následující tabulka popisuje atributy silného názvu.  
  
|Atributy silného názvu|Popis|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Logická hodnota, která určuje, že je použit zpoždění podepsání.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Řetězcová hodnota, která udává název souboru, který obsahuje veřejný klíč (Pokud se používá, zpoždění podepsání) nebo veřejné a soukromé klíče jako parametr předaný konstruktoru tohoto atributu. Všimněte si, název souboru je relativní k cestě výstupní soubor (.exe nebo .dll), není cestu ke zdrojovému souboru.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Označuje kontejner klíče, který obsahuje pár klíčů jako parametr předaný konstruktoru tohoto atributu.|  
  
 Následující příklad kódu ukazuje atributy, které se použijí při použití zpoždění podepsání sestavení se silným názvem vytvořit s soubor veřejného klíče volání `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
