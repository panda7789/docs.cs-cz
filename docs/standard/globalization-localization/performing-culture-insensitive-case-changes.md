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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 844b0edb93b93704c4886495c673dc0496f7ba71
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192974"
---
# <a name="performing-culture-insensitive-case-changes"></a>Provádění změn velikosti písmen nezávisle na jazykové verzi
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, A <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody poskytují přetížení, která nepřijímá žádné parametry. Ve výchozím nastavení, tato přetížení bez parametrů, provést změny velikosti písmen podle hodnoty <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. To vytváří malá a velká písmena výsledky, které se můžou lišit podle jazykové verze. Aby bylo jasné, zda chcete, aby změny velikosti písmen zohledňující jazykovou verzi nebo nezávislých na jazykové verzi, by měla použít přetížení z těchto metod, které vyžadují, abyste s ohledem `culture` parametru. Změny velikosti písmen zohledňující jazykovou verzi, zadejte `CultureInfo.CurrentCulture` pro `culture` parametru. Změny velikosti písmen nezávislých na jazykové verzi, zadejte `CultureInfo.InvariantCulture` pro `culture` parametru.  
  
 Řetězce jsou často, převedeny na standardní případ umožňující snadnější vyhledávání později. Použity tímto způsobem, je třeba zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> by mohl změnit mezi časem, která se změnila tak a době vyhledávání.  
  
 Pokud je rozhodnutí o zabezpečení je založená na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi k zajištění, že výsledek není ovlivněn hodnotou z `CultureInfo.CurrentCulture`. Najdete v části "Řetězec porovnání, které používají aktuální jazykovou verzi" [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak operace s řetězci jazykovou verzi může způsobovat nekonzistentní výsledky.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Pomocí String.ToUpper a String.ToLower – metody  
 Přehlednosti kódu doporučujeme použít vždy přetížení `String.ToUpper` a `String.ToLower` metody, které vám umožňují určit `culture` parametr explicitně. Například následující kód provede vyhledání identifikátoru. `key.ToLower` Operace zohledňující jazykovou verzi ve výchozím nastavení, ale toto chování není jasné z čtení kódu.  
  
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
  
 Pokud chcete, aby `key.ToLower` operace být nezávislá na jazykové verzi, měli byste změnit předchozí příklad následujícím způsobem, aby explicitně `CultureInfo.InvariantCulture` při změně velikosti písma.  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Char.ToUpper – a Char.ToLower – metody  
 I když `Char.ToUpper` a `Char.ToLower` metody mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán) jsou metody, pouze jazykové verze, které tím ovlivníte. Jedná se o pouze dvě jazykových verzích s jedním znakem malých a velkých písmen rozdíly. Další informace o tomto jedinečný mapování velikosti písmen, naleznete v části "Malá a velká písmena" v <xref:System.String> třídě. Pro přehlednost kódu a dosahovat konzistentních výsledků, doporučujeme vždy použijte přetížení těchto metod, které umožňuje explicitně určit `culture` parametru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
