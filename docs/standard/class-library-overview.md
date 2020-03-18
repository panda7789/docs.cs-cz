---
title: Přehled knihovny tříd .NET
ms.date: 02/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], library overview
- classes [.NET Core], library overview
- .NET, library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], F#
- System namespace
- F#, data types
- .NET Framework, class library
- type system [.NET Framework]
- data types [.NET Framework]
- value types
- data types [.NET Framework], Visual Basic
- Common Language Specification
- namespaces [.NET Framework]
- floating point value type
- class library [.NET Framework]
- CLS
- logical value type
- .NET Framework class library, about
- built-in types
- namespaces [.NET Framework], about namespaces
- Visual C++, data types
- members [.NET Framework], type
- data types [.NET Framework], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
ms.openlocfilehash: 596c0fd8fec8f59d977f1db445f9000df23ad5ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400482"
---
# <a name="net-class-library-overview"></a>Přehled knihovny tříd .NET

Implementace .NET zahrnují třídy, rozhraní, delegáty a typy hodnot, které urychlují a optimalizují proces vývoje a poskytují přístup k funkcím systému. Pro usnadnění interoperability mezi jazyky je většina typů .NET kompatibilní se specifikací CLS, a proto je lze použít z libovolného programovacího jazyka, jehož kompilátor odpovídá specifikaci společného jazyka (CLS).  
  
 Typy .NET jsou základem, na kterém jsou vytvořeny aplikace, součásti a ovládací prvky rozhraní .NET. Implementace rozhraní .NET zahrnují typy, které provádějí následující funkce:  
  
- Představují základní datové typy a výjimky.  
  
- Zapouzdření datových struktur.  
  
- Provádět vstupně-výkon.  
  
- Přístup k informacím o načtených typech.  
  
- Vyvolat kontroly zabezpečení rozhraní .NET Framework.  
  
- Poskytněte přístup k datům, bohaté grafické uživatelské rozhraní na straně klienta a grafické uživatelské rozhraní na straně klienta řízené serverem.  
  
 .NET poskytuje bohatou sadu rozhraní, stejně jako abstraktní a konkrétní (neabstraktní) třídy. Můžete použít konkrétní třídy, jak je nebo v mnoha případech odvodit své vlastní třídy z nich. Chcete-li použít funkce rozhraní, můžete buď vytvořit třídu, která implementuje rozhraní nebo odvodit třídu z jedné z tříd .NET, která implementuje rozhraní.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů

 Typy .NET používají schéma pojmenování syntaxe, které označuje hierarchii. Tato technika seskupuje související typy do oborů názvů, aby je bylo možné snadněji prohledávat a odkazovat. První část celého názvu – až po tečku zcela vpravo – je název oboru názvů. Poslední část názvu je název typu. Například `System.Collections.Generic.List<T>` představuje `List<T>` typ, který patří `System.Collections.Generic` do oboru názvů. Typy v <xref:System.Collections.Generic> lze použít pro práci s obecné kolekce.  
  
 Toto schéma pojmenování usnadňuje vývojářům knihoven rozšíření rozhraní .NET Framework k vytvoření hierarchických skupin typů a jejich pojmenování konzistentním a informativním způsobem. Umožňuje také typy jednoznačně identifikovat jejich úplný název (to znamená podle jejich oboru názvů a název typu), který zabraňuje kolizím názvu typu. Očekává se, že vývojáři knihovny budou při vytváření názvů pro obory názvů používat následující konvence:  
  
 *Název společnosti*. *Název technologie*  
  
 Například obor `Microsoft.Word` názvů odpovídá této příručce.  
  
 Použití vzorů pojmenování k seskupení souvisejících typů do oborů názvů je velmi užitečný způsob vytváření a vytváření knihoven tříd dokumentů. Toto schéma pojmenování však nemá žádný vliv na viditelnost, přístup člena, dědičnost, zabezpečení nebo vazbu. Obor názvů lze rozdělit na více sestavení a jedno sestavení může obsahovat typy z více oborů názvů. Sestavení poskytuje formální strukturu pro správu verzí, nasazení, zabezpečení, načítání a viditelnost v za běhu společného jazyka.  
  
 Další informace o oborech názvů a názvech typů naleznete [v tématu Common Type System](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>System – obor názvů

 Obor <xref:System> názvů je kořenový obor názvů pro základní typy v rozhraní .NET. Tento obor názvů zahrnuje třídy, které představují <xref:System.Object> základní datové typy používané <xref:System.Byte>všemi <xref:System.Array> <xref:System.Int32>aplikacemi: (kořen hierarchie dědičnosti), , <xref:System.String> <xref:System.Char>, , a tak dále. Mnoho z těchto typů odpovídají primitivní datové typy, které používá programovací jazyk. Při psaní kódu pomocí typů rozhraní .NET Framework můžete použít odpovídající klíčové slovo vašeho jazyka, když se očekává základní datový typ rozhraní .NET Framework.  
  
 V následující tabulce jsou uvedeny základní typy, které rozhraní .NET poskytuje, stručně popisuje každý typ a označuje odpovídající typ v jazyce Visual Basic, C#, C++ a F#.  
  
|Kategorie|Název třídy|Popis|Datový typ jazyka Visual Basic|Datový typ jazyka C#|Datový typ C++/CLI|Datový typ F#|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Integer|<xref:System.Byte>|Osmibitové celé číslo bez znaménka.|**Byte**|**Bajt**|**unsigned char**|**Bajt**|  
||<xref:System.SByte>|Osmibitové podepsané celé číslo.<br /><br /> Není kompatibilní se standardem CLS.|**Sbyte**|**Sbyte**|**char**<br /> -nebo-<br /> **podepsaný** **znak**|**Sbyte**|  
||<xref:System.Int16>|16bitové podepsané celé číslo.|**Krátké**|**short**|**short**|**int16**|  
||<xref:System.Int32>|32bitové podepsané celé číslo.|**Integer**|**int**|**int**<br /><br /> -nebo-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64bitové podepsané celé číslo.|**Dlouhé**|**long**|**__int64**|**int64**|  
||<xref:System.UInt16>|16bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se standardem CLS.|**UKrátké**|**ushort**|**unsigned short**|**uint16**|  
||<xref:System.UInt32>|32bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se standardem CLS.|**UInteger**|**uint**|**unsigned int**<br /> -nebo-<br /> **unsigned long**|**Uint32**|  
||<xref:System.UInt64>|64bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se standardem CLS.|**ULong (ULong)**|**ulong**|**nepodepsané __int64**|**uint64 řekl:**|  
|Plovoucí desetinná čárka|<xref:System.Single>|Jednopřesné (32bitové) číslo s plovoucí desetinnou desetinnou tácem.|**Single**|**float**|**float**|**plovák32**<br> – nebo –<br>**Jednoho**|  
||<xref:System.Double>|Dvojité přesnost (64bitové) číslo s plovoucí desetinnou desetinnou hlavou.|**Dvojité**|**double**|**double**|**float**<br> – nebo – <br> **double**|  
|Logické|<xref:System.Boolean>|Logická hodnota (true nebo false).|**Logická hodnota**|**bool**|**bool**|**bool**|  
|Ostatní|<xref:System.Char>|Znak Unicode (16 bitů).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Desetinná hodnota (128 bitů).|**Desetinných**|**decimal**|**Desetinných**|**decimal**|  
||<xref:System.IntPtr>|Podepsané celé číslo, jehož velikost závisí na podkladové platformě (32bitová hodnota na 32bitové platformě a 64bitová hodnota na 64bitové platformě).|**Intptr**<br /><br /> Žádný vestavěný typ.|**Intptr**<br /><br /> Žádný vestavěný typ.|**Intptr**<br /><br /> Žádný vestavěný typ.|**unativeint**|  
||<xref:System.UIntPtr>|Nepodepsané celé číslo, jehož velikost závisí na podkladové platformě (32bitová hodnota na 32bitové platformě a 64bitová hodnota na 64bitové platformě).<br /><br /> Není kompatibilní se standardem CLS.|**UIntPtr**<br /><br /> Žádný vestavěný typ.|**UIntPtr**<br /><br /> Žádný vestavěný typ.|**UIntPtr**<br /><br /> Žádný vestavěný typ.|**unativeint**|  
||<xref:System.Object>|Kořen hierarchie objektů.|**Objekt**|**Objekt**|**Objekt^**|**Obj**|  
||<xref:System.String>|Neměnný řetězec znaků Unicode s pevnou délkou.|**Řetězec**|**Řetězec**|**Řetězec^**|**Řetězec**|  
  
 Kromě základních datových typů <xref:System> obsahuje obor názvů více než 100 tříd, od tříd, které zpracovávají výjimky, až po třídy, které se zabývají základními koncepty runtime, jako jsou aplikační domény a systém uvolňování paměti. Obor <xref:System> názvů také obsahuje mnoho oborů názvů druhé úrovně.  
  
 Další informace o oborech názvů získáte v [prohlížeči rozhraní .NET API](https://docs.microsoft.com/dotnet/api) k procházení knihovny tříd .NET. Referenční dokumentace rozhraní API poskytuje dokumentaci ke každému oboru názvů, jeho typům a každému jejich členům.  
  
## <a name="see-also"></a>Viz také

- [Obecný systém typů](../../docs/standard/base-types/common-type-system.md)
- [Prohlížeč rozhraní API .NET](../../api/index.md)
- [Přehled](../../docs/framework/get-started/overview.md)
