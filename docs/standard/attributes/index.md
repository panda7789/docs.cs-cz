---
title: Rozšiřování metadat pomocí atributů
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b3a106eb58de4865e260a43c8466019e738510f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130906"
---
# <a name="extending-metadata-using-attributes"></a>Rozšiřování metadat pomocí atributů
Běžný jazyk runtime umožňuje přidat popisné deklarace podobné klíčovým slovům, nazývané atributy, k přidání tónů programovacích prvků, jako jsou typy, pole, metody a vlastnosti. Při kompilaci kódu pro modul runtime je převeden na zprostředkující jazyk Společnosti Microsoft (MSIL) a umístěn uvnitř přenosného spustitelného souboru (PE) spolu s metadaty generovanými kompilátorem. Atributy umožňují umístit další popisné informace do metadat, které lze extrahovat pomocí služby reflexe modulu runtime. Kompilátor vytvoří atributy při deklarování instancí speciálních tříd, které jsou odvozeny z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Rozhraní .NET Framework používá atributy z různých důvodů a k řešení řady problémů. Atributy popisují, jak serializovat data, určit vlastnosti, které se používají k vynucení zabezpečení a omezit optimalizace kompilátorem just-in-time (JIT), aby kód zůstal snadno laditelný. Atributy můžete také zaznamenat název souboru nebo autorkódu nebo řídit viditelnost ovládacích prvků a členů během vývoje formulářů.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Použití atributů](../../../docs/standard/attributes/applying-attributes.md)|Popisuje, jak použít atribut pro prvek kódu.|  
|[Zápis vlastních atributů](../../../docs/standard/attributes/writing-custom-attributes.md)|Popisuje, jak navrhnout vlastní třídy atributů.|  
|[Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Popisuje, jak načíst vlastní atributy pro kód, který je načten do kontextu spuštění.|  
|[Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)|Obsahuje přehled metadat a popisuje, jak je implementována v přenosném spustitelném souboru rozhraní .NET Framework ( PE).|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Vysvětluje, jak načíst informace o vlastních atributech v kontextu pouze reflexe.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Attribute?displayProperty=nameWithType>
