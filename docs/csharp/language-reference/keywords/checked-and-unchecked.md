---
title: Zkontrolováno a nezkontrolováno - C# odkaz
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a3b1ef8e6d8e496eda74ab25b3fe17f8174bac11
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713721"
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
C#příkazy mohou být provedeny v kontrolovaném nebo nezaškrtnutém kontextu. V kontrolovaném kontextu přetečení aritmetického přetečení vyvolá výjimku. V nekontrolovaném kontextu se aritmetické přetečení ignoruje a výsledek se zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.  
  
- [zaškrtnuté políčko](checked.md) Zadejte kontrolovaný kontext.  
  
- [nezaškrtnuto](unchecked.md) Zadejte nezaškrtnutý kontext.  
  
 Kontrola přetečení má vliv na následující operace:  
  
- Výrazy s použitím následujících předdefinovaných operátorů pro celočíselné typy:  
  
     `++`, `--`, unární `-`, `+`, `-`, `*`, `/`  
  
- Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.  
  
 Pokud není zadána žádná `checked` ani `unchecked`, výchozí kontext pro nekonstantní výrazy (výrazy, které jsou vyhodnocovány za běhu) je definován hodnotou možnosti kompilátoru [zaškrtnuto](../compiler-options/checked-compiler-option.md) . Ve výchozím nastavení je hodnota této možnosti nastavená na hodnotu zrušit a aritmetické operace jsou spouštěny v nekontrolovaném kontextu.
 
 V případě konstantních výrazů (výrazy, které mohou být plně vyhodnocovány v době kompilace) je výchozí kontext vždy zaškrtnuto. Pokud není konstantní výraz explicitně umístěn v nekontrolovaném kontextu, přetečení, ke kterým dojde během kompilace výrazu, způsobují chyby při kompilaci.
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova příkazů](statement-keywords.md)
