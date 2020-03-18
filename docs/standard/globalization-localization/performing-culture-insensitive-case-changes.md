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
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160128"
---
# <a name="performing-culture-insensitive-case-changes"></a>Provádění změn velikosti písmen nezávisle na jazykové verzi
Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, která nepřijímají žádné parametry. Ve výchozím nastavení tato přetížení bez parametrů provádět změny <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>případu na základě hodnoty . To vytváří výsledky rozlišující malá a velká písmena, které se mohou lišit podle jazykové verze. Chcete-li jasně, zda chcete, aby změny případu byly citlivé na jazykovou verzi nebo necitlivé na `culture` jazykovou verzi, měli byste použít přetížení těchto metod, které vyžadují explicitně zadat parametr. Pro změny malých a `CultureInfo.CurrentCulture` velkých `culture` písmen zjitřující jazykovou verzi zadejte pro parametr. Pro změny malých a `CultureInfo.InvariantCulture` velkých `culture` písmen nerozlišující jazykovou verzi zadejte pro parametr.  
  
 Řetězce jsou často převedeny na standardní případ, aby bylo možné později snadněji vyhledat. Při použití řetězců tímto způsobem byste `CultureInfo.InvariantCulture` měli `culture` zadat parametr, <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> protože hodnota může potenciálně změnit mezi čas, kdy je změněn případ a čas, kdy dojde k vyhledávání.  
  
 Pokud je rozhodnutí o zabezpečení založeno na operaci změny případu, operace by měla být necitlivá `CultureInfo.CurrentCulture`na jazykovou verzi, aby bylo zajištěno, že výsledek není ovlivněn hodnotou . Naleznete v části "Porovnání řetězců, které používají aktuální jazykovou verzi" v článku [Doporučené postupy pro použití řetězce](../../../docs/standard/base-types/best-practices-strings.md) pro příklad, který ukazuje, jak mohou operace řetězce citlivé na jazykovou verzi vytvářet nekonzistentní výsledky.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Použití metod String.ToUpper a String.ToLower  
 Pro přehlednost kódu se doporučuje vždy používat `String.ToUpper` přetížení `String.ToLower` a metody, které `culture` umožňují explicitně zadat parametr. Například následující kód provádí vyhledávání identifikátorů. Operace `key.ToLower` je ve výchozím nastavení citlivá na jazykovou verzi, ale toto chování není jasné ze čtení kódu.  
  
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
  
 Pokud `key.ToLower` chcete, aby operace byla necitlivá na jazykovou verzi, měli byste `CultureInfo.InvariantCulture` změnit předchozí příklad takto explicitně použít při změně případu.  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Použití Char.ToUpper a Char.ToLower metody  
 Ačkoli `Char.ToUpper` metody `Char.ToLower` a mají stejné `String.ToUpper` vlastnosti jako metody a, `String.ToLower` jediné kultury, které jsou ovlivněny, jsou turečtina (Turecko) a ázerbájdžánština (latinka, Ázerbájdžán). Jedná se o pouze dvě jazykové verze s rozdíly v tělese s jedním znakem. Další podrobnosti o tomto jedinečném mapování případů naleznete <xref:System.String> v části "Velká písmena" v tématu třídy. Pro srozumitelnost kódu a zajistit konzistentní výsledky, je doporučeno vždy používat přetížení těchto metod, které umožňují explicitně zadat `culture` parametr.  
  
## <a name="see-also"></a>Viz také

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
