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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132844"
---
# <a name="net-class-library-overview"></a>Přehled knihovny tříd .NET

Implementace rozhraní .NET zahrnují třídy, rozhraní, delegáty a typy hodnot, které urychlují a optimalizují proces vývoje a poskytují přístup k funkčnosti systému. Aby bylo možné zajistit vzájemnou funkční spolupráci mezi jazyky, většina typů .NET je kompatibilní se specifikací CLS a lze ji proto použít ze všech programovacích jazyků, jejichž kompilátor odpovídá specifikaci CLS (Common Language Specification).  
  
 Typy .NET jsou základem, ve kterém jsou sestaveny aplikace, komponenty a ovládací prvky .NET. Implementace rozhraní .NET zahrnuje typy, které provádějí následující funkce:  
  
- Představuje základní datové typy a výjimky.  
  
- Zapouzdření datových struktur.  
  
- Provede vstupně-výstupní operace.  
  
- Přístup k informacím o načtených typech.  
  
- Vyvolá .NET Framework kontroly zabezpečení.  
  
- Poskytněte přístup k datům, rozsáhlou datovou řadu na straně klienta a grafické uživatelské rozhraní na straně klienta řízené serverem.  
  
 Rozhraní .NET poskytuje bohatou sadu rozhraní a také abstraktní a konkrétní (neabstraktní) třídy. Konkrétní třídy můžete použít tak, jak jsou, nebo v mnoha případech odvodit z nich vlastní třídy. Chcete-li použít funkci rozhraní, můžete buď vytvořit třídu, která implementuje rozhraní, nebo odvodit třídu z jedné z tříd .NET, která implementuje rozhraní.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů

 Typy .NET používají schéma pojmenování syntaxe tečky, které označuje hierarchii. Tento postup seskupuje související typy do oborů názvů, aby je bylo možné prohledávat a snadněji na něj. První část celého jména – až do pravé tečky – je název oboru názvů. Poslední část názvu je název typu. Například `System.Collections.Generic.List<T>` představuje typ `List<T>`, který patří do oboru názvů `System.Collections.Generic`. Typy v <xref:System.Collections.Generic> lze použít pro práci s obecnými kolekcemi.  
  
 Toto schéma pojmenování usnadňuje vývojářům knihoven rozšíření .NET Framework pro vytváření hierarchických skupin typů a jejich pojmenování konzistentním a informativním způsobem. Umožňuje také jednoznačně identifikovat typy podle jejich úplného názvu (tj. podle jejich oboru názvů a názvu typu), což brání kolizím názvů typů. Při vytváření názvů pro své obory názvů se očekává, že vývojáři knihovny použijí následující konvenci:  
  
 *CompanyName*. *Technologický*  
  
 Například obor názvů `Microsoft.Word` odpovídá tomuto vzoru.  
  
 Použití vzorů pojmenování k seskupení souvisejících typů do oborů názvů je velmi užitečným způsobem pro sestavování a dokumentování knihoven tříd. Toto schéma pojmenování ale nemá žádný vliv na viditelnost, přístup ke členům, dědění, zabezpečení nebo vazby. Obor názvů může být rozdělen mezi více sestavení a jedno sestavení může obsahovat typy z více oborů názvů. Sestavení poskytuje formální strukturu pro správu verzí, nasazení, zabezpečení, načítání a viditelnost v modulu CLR (Common Language Runtime).  
  
 Další informace o oborech názvů a názvech typů naleznete v tématu [Common Type System](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>System – obor názvů

 Obor názvů <xref:System> je kořenovým oborem názvů pro základní typy v rozhraní .NET. Tento obor názvů obsahuje třídy, které reprezentují základní datové typy používané všemi aplikacemi: <xref:System.Object> (kořen hierarchie dědičnosti), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>a tak dále. Mnohé z těchto typů odpovídají primitivním datovým typům, které používá váš programovací jazyk. Když píšete kód pomocí .NET Frameworkch typů, můžete použít klíčové slovo odpovídající vašemu jazyku, když je očekáváno .NET Framework základní datový typ.  
  
 Následující tabulka uvádí základní typy, které poskytuje .NET, stručně popisuje každý typ a označuje odpovídající typ v Visual Basic, C#, C++a. F#  
  
|Kategorie|Název třídy|Popis|Visual Basic datový typ|C#datový typ|C++/CLI – datový typ|F#datový typ|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Integer|<xref:System.Byte>|8 bitů unsigned integer.|**Bytové**|**byte**|**znak bez znaménka**|**byte**|  
||<xref:System.SByte>|8bitové celé číslo se znaménkem.<br /><br /> Není kompatibilní se specifikací CLS.|**SByte**|**sbyte**|**char**<br /> -nebo-<br /> **signed** **char**|**sbyte**|  
||<xref:System.Int16>|16bitové celé číslo se znaménkem.|**Dostatečná**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32 celé číslo se znaménkem.|**Čísla**|**int**|**int**<br /><br /> -nebo-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64 celé číslo se znaménkem.|**Dlouhou**|**long**|**__int64**|**Int64**|  
||<xref:System.UInt16>|16bitová unsigned integer.<br /><br /> Není kompatibilní se specifikací CLS.|**UShort**|**ushort**|**krátký unsigned**|**UInt16**|  
||<xref:System.UInt32>|32 bitová unsigned integer.<br /><br /> Není kompatibilní se specifikací CLS.|**UInteger –**|**uint**|**unsigned int**<br /> -nebo-<br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|64 bitová unsigned integer.<br /><br /> Není kompatibilní se specifikací CLS.|**ULong**|**ulong**|**Nepodepsaný __int64**|**UInt64**|  
|Plovoucí desetinná čárka|<xref:System.Single>|Číslo s plovoucí desetinnou čárkou s jednoduchou přesností (32).|**Konkrétní**|**float**|**float**|**float32**<br> or<br>**single**|  
||<xref:System.Double>|Číslo s plovoucí desetinnou čárkou s dvojitou přesností (64).|**Klepat**|**double**|**double**|**float**<br> or <br> **double**|  
|Biolog|<xref:System.Boolean>|Logická hodnota (true nebo false).|**Datového**|**bool**|**bool**|**bool**|  
|Ostatní|<xref:System.Char>|Znak Unicode (16 bitů).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Desítková hodnota (128).|**Notaci**|**decimal**|**Notaci**|**decimal**|  
||<xref:System.IntPtr>|Celé číslo se znaménkem, jehož velikost závisí na základní platformě (32 hodnota na 32 platformě 64 a na 64 32bitové platformě).|**IntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**IntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**IntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**unativeint –**|  
||<xref:System.UIntPtr>|Unsigned integer, jehož velikost závisí na základní platformě (32 hodnota na 32 platformě a na hodnotě 64-bit na platformě pro 64).<br /><br /> Není kompatibilní se specifikací CLS.|**UIntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**UIntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**UIntPtr**<br /><br /> Není k dispozici žádný předdefinovaný typ.|**unativeint –**|  
||<xref:System.Object>|Kořen hierarchie objektů.|**Předmětů**|**object**|**Objekt ^**|**objektu**|  
||<xref:System.String>|Neměnný řetězec s pevnou délkou znaků Unicode.|**Řetězec**|**string**|**Řetězec ^**|**string**|  
  
 Kromě základních datových typů obsahuje obor názvů <xref:System> více než 100 tříd, od tříd, které zpracovávají výjimky na třídy, které se týkají základních konceptů modulu runtime, jako jsou například domény aplikace a systém uvolňování paměti. Obor názvů <xref:System> obsahuje také mnoho oborů názvů druhé úrovně.  
  
 Další informace o oborech názvů získáte pomocí [prohlížeče rozhraní .NET API](https://docs.microsoft.com/dotnet/api) pro procházení knihovny tříd .NET. Referenční dokumentace k rozhraní API poskytuje dokumentaci pro každý obor názvů, její typy a všechny jejich členy.  
  
## <a name="see-also"></a>Viz také:

- [Obecný systém typů](../../docs/standard/base-types/common-type-system.md)
- [.NET API – prohlížeč](../../api/index.md)
- [Přehled](../../docs/framework/get-started/overview.md)
