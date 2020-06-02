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
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276813"
---
# <a name="performing-culture-insensitive-case-changes"></a>Provádění změn velikosti písmen nezávisle na jazykové verzi
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>Metody, <xref:System.String.ToLower%2A?displayProperty=nameWithType> , <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, které nepřijímají žádné parametry. Ve výchozím nastavení tato přetížení bez parametrů provádějí změny velikosti písmen na základě hodnoty <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> . Výsledkem je, že se rozlišují malá a velká písmena, která se mohou lišit podle jazykové verze. Chcete-li zrušit zaškrtnutí bez ohledu na to, zda mají být změny velikosti písmen závislé na jazykové verzi nebo nezávislé na jazykové verzi, měli byste použít přetížení těchto metod, které vyžadují explicitní zadání `culture` parametru. Pro změny velikosti písmen závislé na jazykové verzi zadejte `CultureInfo.CurrentCulture` `culture` parametr. Pro změny velikosti písmen nezávisle na jazykové verzi zadejte `CultureInfo.InvariantCulture` `culture` parametr.  
  
 Řetězce jsou často převedeny na standardní případ, aby bylo možné později povolit snadnější vyhledávání. Pokud jsou řetězce použity tímto způsobem, je vhodné zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> může potenciálně změnit mezi časem změny případu a časem, kdy k vyhledávání dojde.  
  
 Je-li rozhodnutí o zabezpečení založeno na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi, aby se zajistilo, že výsledek není ovlivněn hodnotou `CultureInfo.CurrentCulture` . V části "porovnání řetězců, které používají aktuální jazykovou verzi" v článku [osvědčené postupy pro použití řetězců](../base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak mohou operace s řetězci závislé na jazykové verzi způsobit nekonzistentní výsledky.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Použití metod String. ToUpper a String. ToLower  
 Pro přehlednost kódu doporučujeme vždy použít přetížení `String.ToUpper` `String.ToLower` metod a, které umožňují `culture` explicitně zadat parametr. Například následující kód provádí vyhledávání identifikátorů. `key.ToLower`Ve výchozím nastavení je operace závislá na jazykové verzi, ale toto chování není jasné z čtení kódu.  
  
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
  
 Pokud chcete, aby `key.ToLower` operace byla nezávislá na jazykové verzi, měli byste změnit předchozí příklad takto, aby explicitně používal `CultureInfo.InvariantCulture` při změně případu.  
  
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
 I když `Char.ToUpper` `Char.ToLower` metody a mají stejné vlastnosti jako `String.ToUpper` `String.ToLower` metody a, jsou to ovlivněny pouze v turečtině (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán). Toto jsou jediné dvě kultury s rozdíly v malých a velkých znacích. Další podrobnosti o tomto jedinečném mapování případu naleznete v části "velikost písmen" v <xref:System.String> tématu třídy. Pro přehlednost kódu a zajištění konzistentních výsledků doporučujeme vždy použít přetížení těchto metod, které vám umožní explicitně zadat `culture` parametr.  
  
## <a name="see-also"></a>Viz také

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](performing-culture-insensitive-string-operations.md)
