---
title: Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 192ac28610f596bc6b6f4ebf1c80962ab2d71cbf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463562"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store
Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] obsahuje rozhraní .NET Framework sadu typů a členů reflexe pro použití v aplikacích pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Tyto typy a členy jsou k dispozici v úplné rozhraní .NET Framework stejně jako v [.NET pro Windows Store apps](https://go.microsoft.com/fwlink/?LinkID=225700). Tento dokument popisuje hlavní rozdíly mezi těmito položkami a jejich protějšky v rozhraní .NET Framework 4 a dřívějších verzích.  
  
 Pokud vytváříte aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], je nutné použít typy a členy reflexe v rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Tyto typy a členy jsou také k dispozici, ačkoli nejsou vyžadovány, pro použití v aplikacích pracovní plochy, takže lze použít stejný kód pro oba typy aplikací.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo a načítání sestavení  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] třída <xref:System.Reflection.TypeInfo> obsahuje některé funkce třídy <xref:System.Type> rozhraní .NET Framework 4. Objekt <xref:System.Type> představuje odkaz na definici typu, zatímco objekt <xref:System.Reflection.TypeInfo> představuje samotnou definici typu. To umožňuje práci s objekty typu <xref:System.Type> bez toho, aby modul runtime musel načíst sestavení, na které odkazují. Získání přidruženého objektu <xref:System.Reflection.TypeInfo> vynutí načtení sestavení.  
  
 Typ <xref:System.Reflection.TypeInfo> obsahuje mnoho členů, jež jsou k dispozici v typu <xref:System.Type>, a mnoho vlastností reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] vrací kolekce objektů <xref:System.Reflection.TypeInfo>. Chcete-li získat objekt <xref:System.Reflection.TypeInfo> z objektu <xref:System.Type>, použijte metodu <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Metody dotazů  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] použijte vlastnosti reflexe, které vrací kolekce typu <xref:System.Collections.Generic.IEnumerable%601>, namísto metod, které vrací pole. Kontexty reflexe mohou pro velká sestavení nebo typy implementovat opožděné procházení těchto kolekcí.  
  
 Vlastnosti reflexe vrací pouze metody deklarované pro daný objekt namísto procházení stromu dědičnosti. Kromě toho nelze pro filtrování použít parametry <xref:System.Reflection.BindingFlags>. Namísto toho filtrování probíhá na vrácené kolekci v uživatelském kódu pomocí dotazů LINQ. Pro objekty reflexe modulu runtime (například výsledek výrazu `typeof(Object)`) je procházení stromu dědičnosti provedeno nejlépe prostřednictvím pomocných metod třídy <xref:System.Reflection.RuntimeReflectionExtensions>. Spotřebitelé objektů z vlastních kontextů reflexe nemohou tyto metody použít a musí strom dědičnosti procházet sami.  
  
## <a name="restrictions"></a>Omezení  
 V aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] je přístup k některým typům a členům rozhraní .NET Framework omezen. Například pomocí objektu [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] nelze volat metody rozhraní .NET Framework, které nejsou zahrnuty v rozhraní <xref:System.Reflection.MethodInfo>. Také některé typy a členy, které nejsou v rámci aplikace pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] považovány za bezpečné, jsou blokovány, jako například typy <xref:System.Runtime.InteropServices.Marshal> a <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal>. Toto omezení se týká pouze typů a členů rozhraní .NET Framework. Váš kód nebo kód třetích stran lze volat jako obvykle.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá typy a členy reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] k načtení metod a vlastností typu <xref:System.Globalization.Calendar>, včetně odvozených metod a vlastností. Chcete-li spustit tento kód, vložte ho do souboru s kódem pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] stránky, která obsahuje [Windows.UI.Xaml.Controls.Textblock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládací prvek s názvem `textblock1` v projektu s názvem reflexe. Pokud je vložit tento kód v projektu s jiným názvem, právě Ujistěte se, že změníte název oboru názvů tak, aby odpovídaly váš projekt.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Aplikace .NET pro Windows Store – podporována rozhraní API](https://go.microsoft.com/fwlink/?LinkID=225700)
