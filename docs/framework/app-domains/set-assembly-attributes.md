---
title: Nastavování atributů sestavení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6c327aad129f685e44f7b456e4ceef8f99fe12b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712597"
---
# <a name="setting-assembly-attributes"></a>Nastavování atributů sestavení
Atributy sestavení jsou hodnoty, které obsahují informace o sestavení. Atributy jsou rozdělené do následujících skupin informace:  
  
-   Atributy identity sestavení.  
  
-   Informační atributy.  
  
-   Atributy manifestu sestavení.  
  
-   Atributy silného názvu.  
  
## <a name="assembly-identity-attributes"></a>Atributy Identity sestavení  
 Tři atributy, společně se silným názvem (Pokud je k dispozici), určují identitu sestavení: název, verzi a jazykovou verzi. Tyto atributy tvoří úplný název sestavení, jsou potřeba při odkazování na sestavení v kódu. Atributy lze nastavit jazykovou verzi a verzi sestavení. Kompilátor nebo [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) nastaví hodnotu názvu, když se vytvoří sestavení, na základě souboru obsahujícího manifest sestavení.  
  
 Následující tabulka popisuje atributy verzi a jazykovou verzi.  
  
|Atribut identity sestavení|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Položka výčtu označující jazykovou verzi, která podporuje sestavení. Sestavení lze také nezávislé na jazykové verzi, označující, že obsahuje prostředky pro výchozí jazykovou verzi. **Poznámka:**  Modul runtime zpracovává libovolné sestavení, který nemá atribut culture nastavena na hodnotu null jako satelitní sestavení. Tato sestavení se vztahují pravidel vazby satelitní sestavení. Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Hodnota, která nastaví atributy sestavení, například zda sestavení lze spustit vedle sebe.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Číselnou hodnotu ve formátu *hlavní*. *vedlejší*. *sestavení*. *Revize* (například 2.4.0.0). Modul common language runtime používá tuto hodnotu k provádění operací vazby v sestavení se silným názvem. **Poznámka:**  Pokud <xref:System.Reflection.AssemblyInformationalVersionAttribute> atribut není použit k sestavení, číslo verze určená <xref:System.Reflection.AssemblyVersionAttribute> používá atribut <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, a <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> vlastnosti.|  
  
 Následující příklad kódu ukazuje, jak použít atributy verzi a jazykovou verzi sestavení.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Informační atributy  
 Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení. Následující tabulka popisuje informační atributy, které můžete použít k sestavení.  
  
|Informační atribut|Popis|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Řetězec určující název společnosti.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Řetězec, hodnota, která určuje informace o autorských právech.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Zadáním čísla verze souboru Win32 řetězcovou hodnotu. Obvykle je výchozí hodnota verze sestavení.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Řetězcová hodnota zadání informací o verzi, která není používána modul common language runtime, jako je číslo verze plného produktu. **Poznámka:**  Pokud tento atribut je použit k sestavení, určuje řetězec lze získat v době běhu pomocí <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> vlastnost. Řetězec se používá také v cestě a registru key určeného tímto <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> vlastnosti.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Řetězcová hodnota zadání informací o produktu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Řetězec, hodnota, která určuje informace o ochranných známkách.|  
  
 Tyto atributy lze zobrazit na stránce vlastností Windows sestavení, nebo je můžete přepsat pomocí **/win32res** – možnost kompilátoru zadat vlastní soubor prostředků Win32.  
  
## <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení  
 Atributy manifestu sestavení můžete použít k zadání informací v manifestu sestavení, včetně názvu, popisu, výchozí aliasu a konfiguraci. Následující tabulka popisuje atributy manifestu sestavení.  
  
|Atribut manifestu sestavení|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Řetězcová hodnota, která konfigurace sestavení, jako je například prodejní nebo ladicí. Modul runtime tuto hodnotu nepoužívá.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Řetězec určující výchozí alias použitého při odkazování na sestavení. Tuto hodnotu poskytuje popisný název, pokud není název samotného sestavení popisný (jako je například hodnota identifikátoru GUID). Tato hodnota může také sloužit jako krátká forma výrazu úplného názvu sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Řetězec určující krátký popis, který shrnuje povahu a účel rozhraní sestavení.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Hodnota řetězce, zadejte popisný název sestavení. Sestavení s názvem comdlg může mít například název společnosti Microsoft běžný ovládací prvek dialogového okna.|  
  
## <a name="strong-name-attributes"></a>Atributy silného názvu  
 Nastavit silný název sestavení, můžete použít atributy silného názvu. Následující tabulka popisuje atributy silného názvu.  
  
|Atributy silného názvu|Popis|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Logická hodnota označující, že je použit dodatečném podepisování.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Řetězec určující název souboru, který obsahuje veřejný klíč (Pokud se používá dodatečném podepisování) nebo veřejné a privátní klíče jako parametr předaný konstruktoru tohoto atributu. Všimněte si, že název souboru není vzhledem k výstupní cesta souboru (.exe nebo .dll), cesta ke zdrojovému souboru.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Určuje kontejner klíčů, který obsahuje pár klíčů, který je předán jako parametr do konstruktoru tohoto atributu.|  
  
 Následující příklad kódu ukazuje atributy, které se použijí při použití zpoždění podepsání k vytvoření sestavení se silným názvem pomocí souboru veřejného klíče volání `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Viz také:
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
