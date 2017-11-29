---
title: "Binární serializace"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a>Binární serializace

Serializace může být definován jako proces ukládání stavu objektu do úložiště média. Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu. Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.

Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu. Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem. Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován. Následující části vysvětlují mechanismu serializace robustní součástí rozhraní .NET a označte několik důležitých funkcí, které vám umožní přizpůsobit proces podle svých potřeb.

> [!NOTE]
> Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Povaha binární serializace umožňuje úpravy soukromé členy uvnitř objekt a proto změny stavu je, jsou doporučené ostatní platformy serializace jako JSON.NET, které fungují na povrchu veřejné rozhraní API.

## <a name="binary-serialization-in-net-core"></a>Binární serializace v .NET Core

.NET core podporuje binární serializace s podmnožinu typů. Zobrazí se seznam podporovaných typů v [Serializovatelné typy části](#serializable-types). Definovanou sadu typy jsou musí být serializovatelný mezi rozhraní .NET Framework 4.5.1 a novější verze rozhraní .NET Core 2.0 a novější verze. Jiné implementace rozhraní .NET, jako je například Mono, nejsou oficiálně podporované, ale také musí být práce.

### <a name="serializable-types"></a>Serializovatelné typy

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <xref:System.DBNull?displayProperty=nameWithType>(k dispozici v .NET Core bodu 2.0.2 a novější)   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <xref:System.ValueTuple?displayProperty=nameWithType>(není serializovatelný v rozhraní .NET Framework 4.7 a starší verze)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a>V tomto oddílu

 [Koncepty serializace](../../../docs/standard/serialization/serialization-concepts.md)  
 Popisuje dva scénáře, kde je serializace užitečná: Pokud zachovává data do úložiště a při předávání objektů mezi doménami aplikace.  
  
 [Základní serializace](../../../docs/standard/serialization/basic-serialization.md)  
 Popisuje, jak používat binárního souboru a SOAP formátovacích modulů k serializaci objektů.  
  
 [Selektivní serializace](../../../docs/standard/serialization/selective-serialization.md)  
 Popisuje, jak zabránit serializována některé členy třídy.  
  
 [Vlastní serializace](../../../docs/standard/serialization/custom-serialization.md)  
 Popisuje, jak přizpůsobit serializace pro třídu pomocí <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
 [Kroky v procesu serializace](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Popisuje kurz akce serializace trvá, když <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda je volána na formátovacím modulem.  
  
 [Verze serializace](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Vysvětluje, jak vytvořit Serializovatelné typy, které lze upravit v čase bez způsobení aplikací k vyvolání výjimky.  
  
 [Pokyny pro serializaci](../../../docs/standard/serialization/serialization-guidelines.md)  
 Poskytuje některé obecné pokyny pro rozhodování, kdy k serializaci objektu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Runtime.Serialization>  
 Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.  
  
## <a name="related-sections"></a>Související oddíly  
 [XML a serializace protokolu SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Popisuje mechanismus serializace XML, který je součástí common language runtime.  
  
 [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)  
 Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.  
  
 [Vzdálených objektů](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.  
  
 [Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Obsahuje témata, která popisují a popisují, jak program webové služby XML vytvořených pomocí technologie ASP.NET.
