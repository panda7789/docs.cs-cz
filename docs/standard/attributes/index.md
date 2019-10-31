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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130906"
---
# <a name="extending-metadata-using-attributes"></a>Rozšiřování metadat pomocí atributů
Modul CLR (Common Language Runtime) umožňuje přidat popisné deklarace podobné klíčovým slovům označované jako atributy, aby bylo možné opatřit poznámkami programovací prvky, jako jsou typy, pole, metody a vlastnosti. Když kompilujete kód pro modul runtime, je převeden do jazyka MSIL (Microsoft Intermediate Language) a umístěn do přenositelného spustitelného souboru (PE) spolu s metadaty generovanými kompilátorem. Atributy umožňují umístit do metadat dodatečné popisné informace, které lze extrahovat pomocí služeb reflexe za běhu. Kompilátor vytvoří atributy při deklaraci instancí speciálních tříd, které jsou odvozeny z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 .NET Framework používá atributy z nejrůznějších důvodů a řeší řadu problémů. Atributy popisují způsob serializace dat, určení vlastností, které se používají k vymáhání zabezpečení, a omezení optimalizace pomocí kompilátoru JIT (just-in-time), takže kód zůstane snadno laděn. Atributy mohou také zaznamenávat název souboru nebo autora kódu nebo ovládat viditelnost ovládacích prvků a členů během vývoje formulářů.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Použití atributů](../../../docs/standard/attributes/applying-attributes.md)|Popisuje, jak použít atribut na prvek kódu.|  
|[Zápis vlastních atributů](../../../docs/standard/attributes/writing-custom-attributes.md)|Popisuje, jak navrhnout vlastní třídy atributů.|  
|[Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Popisuje, jak načíst vlastní atributy pro kód, který je načten do kontextu spuštění.|  
|[Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)|Poskytuje přehled metadat a popisuje, jak je implementováno v .NET Framework přenositelného spustitelného souboru (PE).|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Vysvětluje, jak načíst informace o vlastním atributu v kontextu pouze pro reflexi.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Attribute?displayProperty=nameWithType>
