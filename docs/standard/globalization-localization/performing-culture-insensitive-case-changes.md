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
ms.openlocfilehash: 8f560e3b080f6355d4e0c433c2a2218fbcbc6d72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-case-changes"></a>Provádění změn velikosti písmen nezávisle na jazykové verzi
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, A <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody poskytují přetížení, které nepřijímá žádné parametry. Ve výchozím nastavení, tato přetížení bez parametrů provádí změny velikosti písmen na základě hodnoty z <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. To vytváří malá a velká písmena výsledky, které se mohou lišit podle jazykové verze. Aby bylo jasné, zda chcete změny velikosti písmen zohledňující jazykovou verzi, nebo na jazykové verzi, by měl použít přetížení těchto metod, které vyžadují, abyste explicitně zadáte `culture` parametr. Změny velikosti písmen zohledňující jazykovou verzi, zadejte `CultureInfo.CurrentCulture` pro `culture` parametr. Nezávislé na jazykových změny velikosti písmen, zadejte `CultureInfo.InvariantCulture` pro `culture` parametr.  
  
 Často řetězce jsou převedeny na standardní případ povolit jednodušší vyhledávání později. Pokud řetězce používají tímto způsobem, musíte zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> by mohl změnit mezi časem, která tento případ se změnila a čas, který k vyhledávání.  
  
 Pokud rozhodnutí zabezpečení je založená na operaci případu změnit, operace by měla být nezávislé na jazykových zajistit, že výsledek není ovlivněn hodnotu `CultureInfo.CurrentCulture`. Najdete v části "Řetězec porovnání, použijte aktuální jazykovou verzi" [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) článek pro příklad, který ukazuje, jak operace s řetězci jazykovou verzi může způsobit nekonzistentní výsledky.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Pomocí metod String.ToUpper and String.ToLower  
 Pro přehlednost kódu, se doporučuje použít vždy přetížení `String.ToUpper` a `String.ToLower` metody, které umožňují určit `culture` parametr explicitně. Například následující kód provede vyhledání identifikátoru. `key.ToLower` Operace zohledňující jazykovou verzi ve výchozím nastavení, ale toto chování není jasné z čtení kódu.  
  
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
  
 Pokud chcete `key.ToLower` operace, jazykové verzi, měli byste změnit v předchozím příkladu následujícím způsobem, aby explicitně použít `CultureInfo.InvariantCulture` při změně velikosti písma.  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Pomocí Char.ToUpper a Char.ToLower – metody  
 I když `Char.ToUpper` a `Char.ToLower` metody mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` metody, pouze jazykové verze, které se vztahuje jsou Turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán). Toto jsou pouze dvě jazykové verze s rozdíly délce jednoho znaku velká a malá písmena. Další podrobnosti o tomto jedinečný případu mapování, najdete v části "Malá a velká písmena" v <xref:System.String> třída tématu. Pro přehlednost kódu a dosahovat konzistentních výsledků, doporučujeme vždy použijte přetížení těchto metod, které vám umožní explicitně zadáte `culture` parametr.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
