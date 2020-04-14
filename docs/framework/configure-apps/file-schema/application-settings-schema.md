---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242826"
---
# <a name="application-settings-schema"></a><span data-ttu-id="8ae66-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="8ae66-102">Application Settings schema</span></span>

<span data-ttu-id="8ae66-103">Nastavení aplikace umožňují formulářům systému Windows nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a s rozsahem uživatele.</span><span class="sxs-lookup"><span data-stu-id="8ae66-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="8ae66-104">V tomto kontextu *nastavení* je libovolná část informace, která může být specifická pro aplikaci nebo specifické pro aktuálního uživatele – cokoli od připojovacího řetězce databáze až po upřednostňovanou výchozí velikost okna uživatele.</span><span class="sxs-lookup"><span data-stu-id="8ae66-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="8ae66-105">Ve výchozím nastavení používá nastavení aplikace <xref:System.Configuration.LocalFileSettingsProvider> v aplikaci Windows Forms třídu, která používá konfigurační systém .NET k ukládání nastavení do konfiguračního souboru XML.</span><span class="sxs-lookup"><span data-stu-id="8ae66-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="8ae66-106">Další informace o souborech používaných v nastavení aplikace naleznete v [tématu Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="8ae66-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="8ae66-107">Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.</span><span class="sxs-lookup"><span data-stu-id="8ae66-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="8ae66-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ae66-108">Element</span></span>                    | <span data-ttu-id="8ae66-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8ae66-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="8ae66-110">**\<aplikaceNastavení>**</span><span class="sxs-lookup"><span data-stu-id="8ae66-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="8ae66-111">Obsahuje \*\* \<\*\* všechna nastavení>značky specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ae66-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="8ae66-112">**\<uživatelNastavení>**</span><span class="sxs-lookup"><span data-stu-id="8ae66-112">**\<userSettings>**</span></span>        | <span data-ttu-id="8ae66-113">Obsahuje \*\* \<\*\* všechna nastavení>značky specifické pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="8ae66-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="8ae66-114">**\<nastavení>**</span><span class="sxs-lookup"><span data-stu-id="8ae66-114">**\<setting>**</span></span>             | <span data-ttu-id="8ae66-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ae66-115">Defines a setting.</span></span> <span data-ttu-id="8ae66-116">Podřízená \*\* \<aplikaceNastavení>\*\* nebo \*\* \<userSettings>\*\*.</span><span class="sxs-lookup"><span data-stu-id="8ae66-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="8ae66-117">**\<hodnota>**</span><span class="sxs-lookup"><span data-stu-id="8ae66-117">**\<value>**</span></span>               | <span data-ttu-id="8ae66-118">Definuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ae66-118">Defines a setting's value.</span></span> <span data-ttu-id="8ae66-119">Dítě \*\* \<nastavení>\*\*.</span><span class="sxs-lookup"><span data-stu-id="8ae66-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="8ae66-120">\<applicationNastavení> elementu</span><span class="sxs-lookup"><span data-stu-id="8ae66-120">\<applicationSettings> element</span></span>

<span data-ttu-id="8ae66-121">Tento prvek \*\* \<\*\* obsahuje všechna nastavení>značky, které jsou specifické pro instanci aplikace v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8ae66-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="8ae66-122">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="8ae66-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="8ae66-123">\<userSettings> element</span><span class="sxs-lookup"><span data-stu-id="8ae66-123">\<userSettings> element</span></span>

<span data-ttu-id="8ae66-124">Tento prvek \*\* \<\*\* obsahuje všechna nastavení>značky, které jsou specifické pro uživatele, který aktuálně používá aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ae66-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="8ae66-125">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="8ae66-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="8ae66-126">\<nastavení> prvku</span><span class="sxs-lookup"><span data-stu-id="8ae66-126">\<setting> element</span></span>

<span data-ttu-id="8ae66-127">Tento prvek definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ae66-127">This element defines a setting.</span></span> <span data-ttu-id="8ae66-128">Má následující atributy.</span><span class="sxs-lookup"><span data-stu-id="8ae66-128">It has the following attributes.</span></span>

| <span data-ttu-id="8ae66-129">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ae66-129">Attribute</span></span>        | <span data-ttu-id="8ae66-130">Popis</span><span class="sxs-lookup"><span data-stu-id="8ae66-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="8ae66-131">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="8ae66-131">**name**</span></span>         | <span data-ttu-id="8ae66-132">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8ae66-132">Required.</span></span> <span data-ttu-id="8ae66-133">Jedinečné ID nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ae66-133">The unique ID of the setting.</span></span> <span data-ttu-id="8ae66-134">Nastavení vytvořená prostřednictvím sady `ProjectName.Properties.Settings`Visual Studio jsou uložena s názvem .</span><span class="sxs-lookup"><span data-stu-id="8ae66-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="8ae66-135">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="8ae66-135">**serializeAs**</span></span> | <span data-ttu-id="8ae66-136">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8ae66-136">Required.</span></span> <span data-ttu-id="8ae66-137">Formát, který se má použít pro serializaci hodnoty na text.</span><span class="sxs-lookup"><span data-stu-id="8ae66-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="8ae66-138">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="8ae66-138">Valid values are:</span></span><br><br><span data-ttu-id="8ae66-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="8ae66-139">- `string`.</span></span> <span data-ttu-id="8ae66-140">Hodnota je serializována jako <xref:System.ComponentModel.TypeConverter>řetězec pomocí .</span><span class="sxs-lookup"><span data-stu-id="8ae66-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="8ae66-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="8ae66-141">- `xml`.</span></span> <span data-ttu-id="8ae66-142">Hodnota je serializována pomocí serializace XML.</span><span class="sxs-lookup"><span data-stu-id="8ae66-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="8ae66-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="8ae66-143">- `binary`.</span></span> <span data-ttu-id="8ae66-144">Hodnota je serializována jako binární kódovaný text pomocí binární serializace.</span><span class="sxs-lookup"><span data-stu-id="8ae66-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="8ae66-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="8ae66-145">- `custom`.</span></span> <span data-ttu-id="8ae66-146">Poskytovatel nastavení má vlastní znalosti o tomto nastavení a serializuje a deserializuje jej.</span><span class="sxs-lookup"><span data-stu-id="8ae66-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="8ae66-147">\<prvek> hodnoty</span><span class="sxs-lookup"><span data-stu-id="8ae66-147">\<value> element</span></span>

<span data-ttu-id="8ae66-148">Tento prvek obsahuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ae66-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="8ae66-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ae66-149">Example</span></span>

<span data-ttu-id="8ae66-150">Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení s rozsahem aplikace a dvě nastavení s rozsahem uživatele:</span><span class="sxs-lookup"><span data-stu-id="8ae66-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8ae66-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ae66-151">See also</span></span>

- [<span data-ttu-id="8ae66-152">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="8ae66-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="8ae66-153">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="8ae66-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
