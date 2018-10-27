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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acc51287a8c670da63d0ec421aa232864ea91c2b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185846"
---
# <a name="net-class-library-overview"></a>Přehled knihovny tříd .NET

Implementace .NET zahrnují třídy, rozhraní, delegáty a typy hodnot, které urychlují a optimalizovat proces vývoje a poskytují přístup k funkčnosti systému. Většinu typů .NET pro usnadnění vzájemná funkční spolupráce mezi jazyky, jsou kompatibilní se Specifikací CLS a je proto možné z libovolného programovacího jazyka, jejichž kompilátor odpovídá common language specification (CLS).  
  
 Typy .NET jsou základem, na které .NET jsou postaveny aplikace, komponenty a ovládací prvky. Implementace .NET patří typy, které provádějí následující funkce:  
  
-   Představují základní datové typy a výjimky.  
  
-   Zapouzdření datové struktury.  
  
-   Provádění vstupně-výstupních operací.  
  
-   Přístup k informacím o načtené typy.  
  
-   Vyvolání kontroly zabezpečení rozhraní .NET Framework.  
  
-   Poskytuje přístup k datům, bohaté grafické uživatelské rozhraní na straně klienta a grafické uživatelské rozhraní se správou serveru, na straně klienta.  
  
 .NET nabízí bohatou sadu rozhraní, stejně jako abstraktní a konkrétní (neabstraktní) třídy. Můžete použít konkrétní třídy jako nebo v mnoha případech, vlastní odvozovat z nich. Pokud chcete používat funkce rozhraní, můžete vytvořit třídu, která implementuje rozhraní nebo odvodit třídu z jedné ze tříd .NET, která implementuje rozhraní.  
  
## <a name="naming-conventions"></a>Zásady vytváření názvů

 Typy .NET použijte tečku syntaxe schéma pojmenování s connotes hierarchii. Tato technika skupiny souvisejících typů do oborů názvů, je možné prohledávat a snadněji odkazovat. První část úplný název – až úplně vpravo tečka – je název oboru názvů. Poslední část název je název typu. Například `System.Collections.Generic.List<T>` představuje `List<T>` typ, který patří do `System.Collections.Generic` oboru názvů. Typy v <xref:System.Collections.Generic> lze použít pro práci s obecné kolekce.  
  
 Toto schéma pojmenování usnadňuje vývojářům knihovna rozšíření [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vytvářet hierarchické skupiny typů a pojmenujte je konzistentní a informativní způsobem. Umožňuje také typy musí jednoznačně identifikovat podle jejich úplného názvu (to znamená podle názvu oboru názvů a typ), což zabraňuje kolize názvů typu. Se očekává, že vývojáři knihovny použijte následující konvence při vytváření názvů pro své obory názvů:  
  
 *CompanyName*. *TechnologyName*  
  
 Například obor názvů `Microsoft.Word` odpovídá tomuto.  
  
 Použití vzorů pojmenování pro skupiny související typy do oborů názvů je velmi užitečný způsob, jak vytvářet a třída knihovny dokumentů. Toto schéma pojmenování, ale nemá žádný vliv na viditelnost, přístup ke členu, dědičnost, zabezpečení nebo vazby. Obor názvů lze rozdělit mezi několik sestavení a jediné sestavení může obsahovat typy z více oborů názvů. Sestavení poskytuje formální strukturu pro správu verzí, nasazení, zabezpečení, načítání a viditelnost v modulu common language runtime.  
  
 Další informace o názvech typů a oborů názvů, naleznete v tématu [obecný systém typů](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>System – obor názvů

 <xref:System> Obor názvů je kořenový obor názvů pro základní typy v rozhraní .NET. Tento obor názvů obsahuje třídy, které představují základní datové typy použit všemi aplikacemi: <xref:System.Object> (kořen hierarchie dědičnosti) <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>, a tak dále. Mnohé z těchto typů odpovídají primitivní datové typy, které používá svůj oblíbený programovací jazyk. Při psaní kódu s využitím typy rozhraní .NET Framework, můžete použít váš jazyk odpovídající klíčové slovo při očekávání základní datový typ rozhraní .NET Framework.  
  
 V následující tabulce jsou uvedeny základní typy, .NET poskytuje stručně popisuje všechny typy a označuje odpovídající typ v jazyce Visual Basic, C#, C++ a F #.  
  
|Kategorie|Název třídy|Popis|Datový typ jazyka Visual Basic|Datový typ jazyka C#|C + +/ CLI datový typ|Datový typ F #|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Integer|<xref:System.Byte>|Celé číslo bez znaménka 8 bitů.|**Bajtů**|**byte**|**unsigned char**|**byte**|  
||<xref:System.SByte>|8bitové celé číslo se znaménkem.<br /><br /> Není kompatibilní se Specifikací CLS.|**SByte –**|**sbyte**|**char**<br /> -nebo-<br /> **podepsané** **char**|**sbyte**|  
||<xref:System.Int16>|16bitové celé číslo se znaménkem.|**krátké**|**short**|**short**|**Int16**|  
||<xref:System.Int32>|32bitové celé číslo se znaménkem.|**celé číslo**|**int**|**int**<br /><br /> -nebo-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|64bitové celé číslo se znaménkem.|**Long**|**long**|**__int64**|**Int64**|  
||<xref:System.UInt16>|16bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se Specifikací CLS.|**UShort**|**ushort**|**short bez znaménka**|**UInt16**|  
||<xref:System.UInt32>|32bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se Specifikací CLS.|**Uinteger –**|**uint**|**unsigned int**<br /> -nebo-<br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|64bitové celé číslo bez znaménka.<br /><br /> Není kompatibilní se Specifikací CLS.|**ULong**|**ulong**|**unsigned __int64**|**UInt64**|  
|Plovoucí desetinná čárka|<xref:System.Single>|(32bitová verze) číslo s jednoduchou přesností s plovoucí desetinnou čárkou|**Jeden**|**float**|**float**|**float32**</br> or</br>**single**|  
||<xref:System.Double>|(64-bit) číslo s dvojitou přesnost s plovoucí desetinnou čárkou|**Double**|**double**|**double**|**float**</br> or </br> **double**|  
|Logické|<xref:System.Boolean>|Logická hodnota (true nebo false).|**Datový typ Boolean**|**bool**|**bool**|**bool**|  
|Ostatní|<xref:System.Char>|Znak Unicode (16 bitů).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Desetinná hodnota (128-bit).|**Decimal**|**decimal**|**Decimal**|**decimal**|  
||<xref:System.IntPtr>|Celé číslo se znaménkem, závisí na základní platformě (32 bitů hodnotu na 32bitové platformě) a hodnotu 64-bit na 64bitové platformě.|**IntPtr**<br /><br /> Žádný předdefinovaný typ.|**IntPtr**<br /><br /> Žádný předdefinovaný typ.|**IntPtr**<br /><br /> Žádný předdefinovaný typ.|**unativeint –**|  
||<xref:System.UIntPtr>|Celé číslo bez znaménka, závisí na základní platformě (32 bitů hodnotu na 32bitové platformě) a hodnotu 64-bit na 64bitové platformě.<br /><br /> Není kompatibilní se Specifikací CLS.|**UIntPtr**<br /><br /> Žádný předdefinovaný typ.|**UIntPtr**<br /><br /> Žádný předdefinovaný typ.|**UIntPtr**<br /><br /> Žádný předdefinovaný typ.|**unativeint –**|  
||<xref:System.Object>|Kořenový objekt hierarchie.|**objekt**|**object**|**Object^**|**obj**|  
||<xref:System.String>|Neměnné a pevnou délkou řetězec znaků Unicode.|**řetězec**|**string**|**Řetězec ^**|**string**|  
  
 Kromě základních datových typů <xref:System> obor názvů obsahuje více než 100 třídy od třídy, které zpracovávají výjimky z třídy, které se zabývají základní koncepty runtime, jako je například domény aplikace a systému uvolňování paměti. <xref:System> Obor názvů také obsahuje mnoho oborů názvů druhé úrovně.  
  
 Další informace o oborech názvů, použijte [.NET API Browseru](https://docs.microsoft.com/dotnet/api) procházet knihovny tříd rozhraní .NET. Referenční dokumentace rozhraní API poskytuje dokumentaci pro každý obor názvů, jeho typy a všech jejich členy.  
  
## <a name="see-also"></a>Viz také:

- [Obecný systém typů](../../docs/standard/base-types/common-type-system.md)  
- [Prohlížeč rozhraní API .NET](https://docs.microsoft.com/dotnet/api)  
- [Přehled](../../docs/framework/get-started/overview.md)
