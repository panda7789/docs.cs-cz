---
title: Přístup k vlastním atributům
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: a5651e9dc8cf40e737dd523ec5d29e876a9c0765
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130303"
---
# <a name="accessing-custom-attributes"></a>Přístup k vlastním atributům
Po přiřazení atributů k prvkům programu lze reflexi použít k dotazování jejich existence a hodnot. V .NET Framework verze 1,0 a 1,1 jsou vlastní atributy zkontrolovány v kontextu spuštění. .NET Framework verze 2,0 poskytuje nový kontext zatížení, kontext pouze pro reflexi, který lze použít k prohlédnutí kódu, který nelze načíst ke spuštění.  
  
## <a name="the-reflection-only-context"></a>Kontext pouze pro reflexi  
 Kód načtený do kontextu pouze pro reflexi nelze provést. To znamená, že instance vlastních atributů nelze vytvořit, protože by vyžadovaly provádění jejich konstruktorů. Chcete-li načíst a ověřit vlastní atributy v kontextu pouze pro reflexi, použijte třídu <xref:System.Reflection.CustomAttributeData>. Instance této třídy lze získat pomocí vhodného přetížení metody static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>. Viz [Postupy: načtení sestavení do kontextu pouze pro reflexi](how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Kontext spuštění  
 Hlavní metody reflexe pro dotazování atributů v kontextu spuštění jsou <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Přístupnost vlastního atributu je zkontrolována s ohledem na sestavení, ve kterém je připojen. To je ekvivalentní k kontrole, zda metoda na typu v sestavení, ve kterém je vlastní atribut připojen, může volat konstruktor vlastního atributu.  
  
 Metody jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> kontrolují viditelnost a přístupnost argumentu typu. Pouze kód v sestavení, které obsahuje uživatelsky definovaný typ, může načíst vlastní atribut tohoto typu pomocí **GetCustomAttributes**.  
  
 Následující C# příklad je typický vzor návrhu vlastního atributu. Znázorňuje model reflexe vlastního atributu modulu runtime.  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Pokud se modul runtime pokouší načíst vlastní atributy pro typ vlastního atributu Public <xref:System.ComponentModel.DescriptionAttribute> připojen k metodě **GetLanguage** , provede následující akce:  
  
1. Modul runtime kontroluje, zda je argument typu DescriptionAttribute **typu. GetCustomAttributes** *(typ typu) veřejný*, a proto je viditelný a přístupný.  
  
2. Modul runtime kontroluje, zda je uživatelem definovaný typ **MyDescriptionAttribute** , který je odvozen z **DescriptionAttribute** , viditelný a přístupný v rámci sestavení **System. Web. dll** , kde je připojen k metodě **GetLanguage** ().  
  
3. Modul runtime kontroluje, zda je konstruktor třídy **MyDescriptionAttribute** viditelný a přístupný v rámci sestavení **System. Web. dll** .  
  
4. Modul runtime volá konstruktor třídy **MyDescriptionAttribute** s parametry vlastního atributu a vrátí nový objekt volajícímu.  
  
 Model reflexe vlastního atributu by mohl navrácení instancí uživatelsky definovaných typů mimo sestavení, ve kterém je definován typ. Neliší se od členů v běhové systémové knihovně, které vracejí instance uživatelsky definovaných typů, například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole objektů **RuntimeMethodInfo** . Chcete-li klientovi zabránit v zjišťování informací o typu vlastního atributu definovaného uživatelem, definujte členy typu, které mají být NonPublic.  
  
 Následující příklad ukazuje základní způsob použití reflexe k získání přístupu k vlastním atributům.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](viewing-type-information.md)
- [Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md)
