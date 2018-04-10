---
title: Rozšiřování metadat pomocí atributů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, extending
- attributes [.NET Framework], metadata
- elements [.NET Framework], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae399e5213c95b29736c54fcc48ac45a778ba25b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="extending-metadata-using-attributes"></a>Rozšiřování metadat pomocí atributů
Modul common language runtime umožňuje přidat popisné deklarace podobné klíčovým slovům volá atributy umožňuje anotaci elementům programování, jako jsou typy, pole, metod a vlastností. Při kompilaci kódu pro modul runtime, je převést na Microsoft (MSIL intermediate language) a umístěn uvnitř přenosné spustitelný soubor (PE) společně s generované kompilátorem metadat. Atributy umožňují umístit další popisné informace do metadat, které mohou být extrahovány pomocí reflexe služby modulu runtime. Kompilátor vytvoří atributy, když je deklarovat instance speciálních tříd, které jsou odvozeny od <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Rozhraní .NET Framework používá atributy z různých důvodů a vyřešit řadu problémů. Atributy popisují, jak k serializaci dat, zadejte charakteristiky, které slouží k vynucení zabezpečení a omezují optimalizace kompilátoru za běhu (JIT), stále snadno ladit kód. Atributy můžete také zaznamenejte název souboru nebo autora kódu nebo řízení zobrazení ovládacích prvků a členy během vývoje formulářů.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Použití atributů](../../../docs/standard/attributes/applying-attributes.md)|Popisuje, jak se má použít atribut pro element kódu.|  
|[Zápis vlastních atributů](../../../docs/standard/attributes/writing-custom-attributes.md)|Popisuje, jak navrhnout vlastní třídy atributů.|  
|[Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Popisuje, jak získat vlastní atributy pro kód, který je načten do kontextu spuštění.|  
|[Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)|Poskytuje přehled metadat a popisuje, jak jsou implementované v rozhraní .NET Framework přenosné spustitelný soubor (PE) souboru.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Vysvětluje, jak načíst informace o vlastních atributů v kontextu pouze pro reflexi.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Attribute?displayProperty=nameWithType>
