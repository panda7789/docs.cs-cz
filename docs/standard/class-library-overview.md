---
title: ".NET Framework – přehled knihovny tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], JScript
- System namespace
- JScript, data types
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 607ef0020e15581c6ccca8f232eaea6be547f63b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-framework-class-library-overview"></a>.NET Framework – přehled knihovny tříd
[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Zahrnuje třídy, rozhraní a typy hodnot, které urychlit a optimalizovat proces vývoje a poskytují přístup k funkci systému. Většina typů rozhraní .NET Framework usnadňuje vzájemná funkční spolupráce mezi jazyky jsou kompatibilní se specifikací CLS a proto lze z žádný programovací jazyk, jehož kompilátoru vyhovuje specifikace (CLS).  
  
 Typy rozhraní .NET Framework nejsou foundation, na které .NET jsou vytvořeny aplikací, komponent a ovládací prvky. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Obsahuje typy, které provádějí následující funkce:  
  
-   Představují základní datové typy a výjimky.  
  
-   Zapouzdření datové struktury.  
  
-   Proveďte vstupně-výstupní operace.  
  
-   Přístup k informacím o načtené typy.  
  
-   Vyvolání rozhraní .NET Framework kontrol zabezpečení.  
  
-   Poskytnout přístup k datům, bohaté grafické uživatelské rozhraní klienta a řídí serveru, klienta grafickým uživatelským rozhraním.  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Poskytuje bohatou sadu rozhraní, stejně jako abstraktní a konkrétní třídy (jinou než abstraktní). Můžete použít konkrétní třídy, jako je nebo v mnoha případech, vlastní odvozovat z nich. Pokud chcete používat funkci rozhraní, můžete vytvořit třídu, která implementuje rozhraní nebo odvození třídy z jednoho z tříd rozhraní .NET Framework, která implementuje rozhraní.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů  
 Typy rozhraní .NET framework využívají schéma, connotes hierarchie. Tato technika skupin souvisejících typů do oborů názvů, aby mohl být vyhledávat a snadněji odkazovat. První část úplný název – až úplně vpravo tečky – je název oboru názvů. Poslední část názvu je název typu. Například **System.Collections.ArrayList** představuje **ArrayList** typ, který patří do **System.Collections** oboru názvů. Typy v **System.Collections** lze použít k manipulaci s kolekce objektů.  
  
 Toto schéma pojmenování usnadňuje vývojářům knihovny rozšíření [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vytvářet hierarchické skupiny typů a název je konzistentní, informativní způsobem. Umožňuje také typy musí jednoznačně identifikovat podle názvu jejich úplná (to znamená, podle názvu jejich obor názvů a typ), která brání kolize názvů typu. Knihovna vývojáři očekává se, že při vytváření názvů pro jejich obory názvů použít následující konvence:  
  
 *NázevSpolečnosti*. *TechnologyName*  
  
 Například obor názvů Microsoft.Word odpovídá tomuto.  
  
 Použití vzory pojmenování do skupiny související typy do oborů názvů je velmi užitečný způsob vytváření a dokumentování knihovny tříd. Toto schéma pojmenování však nemá žádný vliv na viditelnost, přístup ke členu, dědičnosti, zabezpečení nebo vazby. Obor názvů, může být rozdělený napříč více sestavení a jednoho sestavení může obsahovat typy z více obory názvů. Sestavení poskytuje formální struktura pro správu verzí, nasazení, zabezpečení, načítání a viditelnost v modulu CLR.  
  
 Další informace o názvech obory názvů a typ najdete v tématu [obecný systém typů](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Namespace systému  
 <xref:System> Obor názvů je kořenový obor názvů pro základní typy v [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Tento obor názvů obsahuje třídy, které představují základní datové typy používané všemi aplikacemi: <xref:System.Object> (kořen hierarchie dědičnosti), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>a tak dále. Mnoho z těchto typů odpovídají primitivní datové typy, které používá programovací jazyk. Při psaní kódu pomocí typy rozhraní .NET Framework, můžete použít svůj jazyk odpovídající – klíčové slovo při je očekávána základní datový typ rozhraní .NET Framework.  
  
 Následující tabulka uvádí základní typy, které [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] poskytuje, stručně popisuje každý typ a označuje odpovídající typ v jazyce Visual Basic, C#, C++ a JScript.  
  
|Kategorie|Název třídy|Popis|Datový typ jazyka Visual Basic|Datový typ C#|C++ – datový typ|JScript datový typ|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Integer|<xref:System.Byte>|8bitové celé číslo bez znaménka.|**Bajtů**|**byte**|**unsigned char**|**Bajtů**|  
||<xref:System.SByte>|Celé číslo podepsaný 8 bitů.<br /><br /> Není kompatibilní se specifikací CLS.|**SByte –**|**sbyte**|**char**<br /><br /> -nebo-<br /><br /> **podepsané** **char**|**SByte –**|  
||<xref:System.Int16>|16bitové znaménkem.|**Krátký**|**short**|**short**|**short**|  
||<xref:System.Int32>|32-bit znaménkem.|**Celé číslo**|**int**|**int**<br /><br /> -nebo-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64bitová verze znaménkem.|**Dlouhá**|**long**|**__int64**|**long**|  
||<xref:System.UInt16>|16bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se specifikací CLS.|**Ushort –**|**ushort**|**short bez znaménka**|**UInt16**|  
||<xref:System.UInt32>|32bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se specifikací CLS.|**Uinteger –**|**uint**|**int bez znaménka**<br /><br /> -nebo-<br /><br /> **dlouho bez znaménka**|**UInt32**|  
||<xref:System.UInt64>|64bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se specifikací CLS.|**Ulong –**|**ulong**|**__int64 bez znaménka**|**UInt64**|  
|Plovoucí desetinné čárky|<xref:System.Single>|(32 bitů) číslo s jednoduchou přesností s plovoucí desetinnou čárkou|**Jeden**|**float**|**float**|**float**|  
||<xref:System.Double>|(64 bitů) číslo s dvojitou přesností s plovoucí desetinnou čárkou|**Double**|**double**|**double**|**double**|  
|Logické|<xref:System.Boolean>|Logická hodnota (true nebo false).|**Logická hodnota**|**bool**|**bool**|**bool**|  
|Ostatní|<xref:System.Char>|Znak Unicode (16 bitů).|**Char –**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Desetinnou hodnotu (128-bit).|**Decimal**|**decimal**|**Decimal**|**Decimal**|  
||<xref:System.IntPtr>|Znaménkem jejíž aktuální velikost závisí na základní platformě (32bitová verze hodnota na 32bitové platformě) a hodnota 64bitová verze na 64bitovou platformu.|**IntPtr**<br /><br /> Žádné předdefinované typu.|**IntPtr**<br /><br /> Žádné předdefinované typu.|**IntPtr**<br /><br /> Žádné předdefinované typu.|**IntPtr**|  
||<xref:System.UIntPtr>|Celé číslo bez znaménka jejíž aktuální velikost závisí na základní platformě (32bitová verze hodnota na 32bitové platformě) a hodnota 64bitová verze na 64bitovou platformu.<br /><br /> Není kompatibilní se specifikací CLS.|**UIntPtr**<br /><br /> Žádné předdefinované typu.|**UIntPtr**<br /><br /> Žádné předdefinované typu.|**UIntPtr**<br /><br /> Žádné předdefinované typu.|**UIntPtr**|  
ASS objekty|<xref:System.Object>|Kořen hierarchie objektů.|**Objekt**|**object**|**Objekt\***|**Objekt**|  
||<xref:System.String>|Neměnné, pevnou délkou řetězec znaků Unicode.|**Řetězec**|**string**|**Řetězec\***|**Řetězec**|  
  
 Kromě základních datových typů <xref:System> obor názvů obsahuje více než 100 tříd ze třídy, které zpracování výjimek na třídy, které pracují s základní koncepty runtime, například aplikační domény a uvolňování paměti. <xref:System> Názvů také obsahuje mnoho oborů názvů druhé úrovně.  
  
 Další informace o oborech názvů, přejděte [knihovna tříd rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195). Referenční dokumentaci k nástroji poskytuje stručný přehled každý obor názvů, a také formální popis každého typu a její členy.  
  
## <a name="see-also"></a>Viz také  
 [Obecný systém typů](../../docs/standard/base-types/common-type-system.md)  
 [Knihovna tříd rozhraní .NET framework](http://go.microsoft.com/fwlink/?LinkID=227195)  
 [Přehled](../../docs/framework/get-started/overview.md)
