---
title: Provádění změn velikosti písmen nezávisle na jazykové verzi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: b5289074724e3afd7356599738eeba648f25ca06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120851"
---
# <a name="performing-culture-insensitive-case-changes"></a>Provádění změn velikosti písmen nezávisle na jazykové verzi
Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, která nepřijímají žádné parametry. Ve výchozím nastavení tato přetížení bez parametrů mění velikost písmen v závislosti na hodnotě <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Výsledkem je, že se rozlišují malá a velká písmena, která se mohou lišit podle jazykové verze. Chcete-li zrušit zaškrtnutí bez ohledu na to, zda mají být změny velikosti písmen závislé na jazykové verzi nebo nezávislé na jazykové verzi, měli byste použít přetížení těchto metod, které vyžadují explicitní určení `culture` parametr. Pro změny velikosti písmen závislé na jazykové verzi zadejte `CultureInfo.CurrentCulture` pro parametr `culture`. U změn velikosti písmen nezávisle na jazykové verzi zadejte `CultureInfo.InvariantCulture` pro parametr `culture`.  
  
 Řetězce jsou často převedeny na standardní případ, aby bylo možné později povolit snadnější vyhledávání. Pokud jsou řetězce použity tímto způsobem, je vhodné zadat `CultureInfo.InvariantCulture` pro parametr `culture`, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> může být možné měnit mezi časem změny případu a časem, kdy k vyhledávání dojde.  
  
 Je-li rozhodnutí o zabezpečení založeno na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi, aby se zajistilo, že výsledek není ovlivněn hodnotou `CultureInfo.CurrentCulture`. V části "porovnání řetězců, které používají aktuální jazykovou verzi" v článku [osvědčené postupy pro použití řetězců](../../../docs/standard/base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak mohou operace s řetězci závislé na jazykové verzi způsobit nekonzistentní výsledky.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Použití metod String. ToUpper a String. ToLower  
 Pro přehlednost kódu doporučujeme vždy použít přetížení `String.ToUpper` a `String.ToLower` metody, které umožňují explicitně zadat `culture` parametr. Například následující kód provádí vyhledávání identifikátorů. Ve výchozím nastavení je operace `key.ToLower` citlivá na jazykovou verzi, ale toto chování není jasné z čtení kódu.  
  
### <a name="example"></a>Příklad  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 Pokud chcete, aby operace `key.ToLower` byla nezávislá na jazykové verzi, změňte předchozí příklad takto, aby při změně velikosti písmen explicitně používal `CultureInfo.InvariantCulture`.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Použití metod Char. ToUpper a Char. ToLower  
 I když metody `Char.ToUpper` a `Char.ToLower` mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` metody, jsou tu ovlivněny pouze takové jazykové verze: Turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán). Toto jsou jediné dvě kultury s rozdíly v malých a velkých znacích. Další podrobnosti o tomto jedinečném mapování případu naleznete v části "velikost písmen" v tématu <xref:System.String> třídy. Pro přehlednost kódu a zajištění konzistentních výsledků doporučujeme vždy použít přetížení těchto metod, které vám umožní explicitně zadat `culture` parametr.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
