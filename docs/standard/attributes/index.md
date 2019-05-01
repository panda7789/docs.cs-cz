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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a31082604048e71ebc7581b36857a8bfbd333c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969790"
---
# <a name="extending-metadata-using-attributes"></a>Rozšiřování metadat pomocí atributů
Modul common language runtime vám umožní přidávat popisné deklarace podobné klíčovým slovům, volá se, atributy, opatřit programovací prvky, jako jsou typy, pole, metody a vlastnosti. Při kompilaci kódu pro modul runtime, je převeden na jazyk Microsoft intermediate language (MSIL) a umístit do přenosného spustitelného souboru (PE) spolu s metadat generovaný kompilátorem. Atributy umožňují umístit další popisné informace do metadata, která může být extrahována pomocí služeb reflexe runtime. Kompilátor vytvoří atributy při deklaraci instance speciální tříd, které jsou odvozeny z <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Rozhraní .NET Framework používá atributy pro celou řadu důvodů a vyřešit řadu problémů. Atributy popisují, jak k serializaci dat, zadejte vlastnosti, které slouží k vynucení zabezpečení a omezit optimalizace kompilátor just-in-time (JIT), tak zůstane usnadňuje ladění kódu. Atributy můžete také poznamenejte název souboru nebo autor kódu nebo řízení viditelnosti ovládacích prvků a členů během vývoje formulářů.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Použití atributů](../../../docs/standard/attributes/applying-attributes.md)|Popisuje, jak použít atribut na prvek kódu.|  
|[Zápis vlastních atributů](../../../docs/standard/attributes/writing-custom-attributes.md)|Popisuje postup návrhu vlastní atribut třídy.|  
|[Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Popisuje, jak získat vlastní atributy pro kód, který je načten do kontextu spuštění.|  
|[Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)|Poskytuje přehled o metadata a popisuje, jak je implementován v rozhraní .NET Framework přenosné spustitelné (PE) souboru.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Vysvětluje, jak načíst informace o vlastních atributů v kontextu pouze pro reflexi.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Attribute?displayProperty=nameWithType>
