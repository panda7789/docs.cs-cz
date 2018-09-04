---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514486"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="13548-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="13548-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="13548-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="13548-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="13548-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="13548-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="13548-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="13548-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="13548-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-106">Tables</span></span>  
  
-   <span data-ttu-id="13548-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-107">Columns</span></span>  
  
-   <span data-ttu-id="13548-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-108">Procedures</span></span>  
  
-   <span data-ttu-id="13548-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="13548-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="13548-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="13548-110">Catalog</span></span>  
  
-   <span data-ttu-id="13548-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="13548-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-112">Tables</span></span>  
  
|<span data-ttu-id="13548-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-113">ColumnName</span></span>|<span data-ttu-id="13548-114">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-115">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-116">String</span><span class="sxs-lookup"><span data-stu-id="13548-116">String</span></span>|  
|<span data-ttu-id="13548-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-118">String</span><span class="sxs-lookup"><span data-stu-id="13548-118">String</span></span>|  
|<span data-ttu-id="13548-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-119">TABLE_NAME</span></span>|<span data-ttu-id="13548-120">String</span><span class="sxs-lookup"><span data-stu-id="13548-120">String</span></span>|  
|<span data-ttu-id="13548-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-121">TABLE_TYPE</span></span>|<span data-ttu-id="13548-122">String</span><span class="sxs-lookup"><span data-stu-id="13548-122">String</span></span>|  
|<span data-ttu-id="13548-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-123">TABLE_GUID</span></span>|<span data-ttu-id="13548-124">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-124">Guid</span></span>|  
|<span data-ttu-id="13548-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-125">DESCRIPTION</span></span>|<span data-ttu-id="13548-126">String</span><span class="sxs-lookup"><span data-stu-id="13548-126">String</span></span>|  
|<span data-ttu-id="13548-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-127">TABLE_PROPID</span></span>|<span data-ttu-id="13548-128">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-128">Int64</span></span>|  
|<span data-ttu-id="13548-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-129">DATE_CREATED</span></span>|<span data-ttu-id="13548-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-130">DateTime</span></span>|  
|<span data-ttu-id="13548-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-131">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="13548-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-133">Columns</span></span>  
  
|<span data-ttu-id="13548-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-134">ColumnName</span></span>|<span data-ttu-id="13548-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-136">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-137">String</span><span class="sxs-lookup"><span data-stu-id="13548-137">String</span></span>|  
|<span data-ttu-id="13548-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-139">String</span><span class="sxs-lookup"><span data-stu-id="13548-139">String</span></span>|  
|<span data-ttu-id="13548-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-140">TABLE_NAME</span></span>|<span data-ttu-id="13548-141">String</span><span class="sxs-lookup"><span data-stu-id="13548-141">String</span></span>|  
|<span data-ttu-id="13548-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-142">COLUMN_NAME</span></span>|<span data-ttu-id="13548-143">String</span><span class="sxs-lookup"><span data-stu-id="13548-143">String</span></span>|  
|<span data-ttu-id="13548-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-144">COLUMN_GUID</span></span>|<span data-ttu-id="13548-145">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-145">Guid</span></span>|  
|<span data-ttu-id="13548-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-146">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-147">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-147">Int64</span></span>|  
|<span data-ttu-id="13548-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-149">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-149">Int64</span></span>|  
|<span data-ttu-id="13548-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="13548-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-151">Boolean</span></span>|  
|<span data-ttu-id="13548-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="13548-153">String</span><span class="sxs-lookup"><span data-stu-id="13548-153">String</span></span>|  
|<span data-ttu-id="13548-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="13548-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="13548-155">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-155">Int64</span></span>|  
|<span data-ttu-id="13548-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="13548-156">IS_NULLABLE</span></span>|<span data-ttu-id="13548-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-157">Boolean</span></span>|  
|<span data-ttu-id="13548-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-158">DATA_TYPE</span></span>|<span data-ttu-id="13548-159">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-159">Int32</span></span>|  
|<span data-ttu-id="13548-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-160">TYPE_GUID</span></span>|<span data-ttu-id="13548-161">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-161">Guid</span></span>|  
|<span data-ttu-id="13548-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="13548-163">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-163">Int64</span></span>|  
|<span data-ttu-id="13548-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="13548-165">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-165">Int64</span></span>|  
|<span data-ttu-id="13548-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="13548-167">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-167">Int32</span></span>|  
|<span data-ttu-id="13548-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="13548-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="13548-169">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-169">Int16</span></span>|  
|<span data-ttu-id="13548-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="13548-171">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-171">Int64</span></span>|  
|<span data-ttu-id="13548-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="13548-173">String</span><span class="sxs-lookup"><span data-stu-id="13548-173">String</span></span>|  
|<span data-ttu-id="13548-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="13548-175">String</span><span class="sxs-lookup"><span data-stu-id="13548-175">String</span></span>|  
|<span data-ttu-id="13548-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="13548-177">String</span><span class="sxs-lookup"><span data-stu-id="13548-177">String</span></span>|  
|<span data-ttu-id="13548-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="13548-179">String</span><span class="sxs-lookup"><span data-stu-id="13548-179">String</span></span>|  
|<span data-ttu-id="13548-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="13548-181">String</span><span class="sxs-lookup"><span data-stu-id="13548-181">String</span></span>|  
|<span data-ttu-id="13548-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-182">COLLATION_NAME</span></span>|<span data-ttu-id="13548-183">String</span><span class="sxs-lookup"><span data-stu-id="13548-183">String</span></span>|  
|<span data-ttu-id="13548-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="13548-185">String</span><span class="sxs-lookup"><span data-stu-id="13548-185">String</span></span>|  
|<span data-ttu-id="13548-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="13548-187">String</span><span class="sxs-lookup"><span data-stu-id="13548-187">String</span></span>|  
|<span data-ttu-id="13548-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-188">DOMAIN_NAME</span></span>|<span data-ttu-id="13548-189">String</span><span class="sxs-lookup"><span data-stu-id="13548-189">String</span></span>|  
|<span data-ttu-id="13548-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-190">DESCRIPTION</span></span>|<span data-ttu-id="13548-191">String</span><span class="sxs-lookup"><span data-stu-id="13548-191">String</span></span>|  
|<span data-ttu-id="13548-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="13548-192">COLUMN_LCID</span></span>|<span data-ttu-id="13548-193">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-193">Int32</span></span>|  
|<span data-ttu-id="13548-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="13548-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="13548-195">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-195">Int32</span></span>|  
|<span data-ttu-id="13548-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="13548-196">COLUMN_SORTID</span></span>|<span data-ttu-id="13548-197">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-197">Int32</span></span>|  
|<span data-ttu-id="13548-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="13548-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="13548-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="13548-199">Byte[]</span></span>|  
|<span data-ttu-id="13548-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="13548-200">IS_COMPUTED</span></span>|<span data-ttu-id="13548-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="13548-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-202">Procedures</span></span>  
  
|<span data-ttu-id="13548-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-203">ColumnName</span></span>|<span data-ttu-id="13548-204">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="13548-206">String</span><span class="sxs-lookup"><span data-stu-id="13548-206">String</span></span>|  
|<span data-ttu-id="13548-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="13548-208">String</span><span class="sxs-lookup"><span data-stu-id="13548-208">String</span></span>|  
|<span data-ttu-id="13548-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="13548-210">String</span><span class="sxs-lookup"><span data-stu-id="13548-210">String</span></span>|  
|<span data-ttu-id="13548-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="13548-212">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-212">Int16</span></span>|  
|<span data-ttu-id="13548-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="13548-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="13548-214">String</span><span class="sxs-lookup"><span data-stu-id="13548-214">String</span></span>|  
|<span data-ttu-id="13548-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-215">DESCRIPTION</span></span>|<span data-ttu-id="13548-216">String</span><span class="sxs-lookup"><span data-stu-id="13548-216">String</span></span>|  
|<span data-ttu-id="13548-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-217">DATE_CREATED</span></span>|<span data-ttu-id="13548-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-218">DateTime</span></span>|  
|<span data-ttu-id="13548-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-219">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="13548-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="13548-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="13548-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-222">ColumnName</span></span>|<span data-ttu-id="13548-223">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="13548-225">String</span><span class="sxs-lookup"><span data-stu-id="13548-225">String</span></span>|  
|<span data-ttu-id="13548-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="13548-227">String</span><span class="sxs-lookup"><span data-stu-id="13548-227">String</span></span>|  
|<span data-ttu-id="13548-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="13548-229">String</span><span class="sxs-lookup"><span data-stu-id="13548-229">String</span></span>|  
|<span data-ttu-id="13548-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-230">PARAMETER_NAME</span></span>|<span data-ttu-id="13548-231">String</span><span class="sxs-lookup"><span data-stu-id="13548-231">String</span></span>|  
|<span data-ttu-id="13548-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-233">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-233">Int32</span></span>|  
|<span data-ttu-id="13548-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="13548-235">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-235">Int32</span></span>|  
|<span data-ttu-id="13548-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="13548-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-237">Boolean</span></span>|  
|<span data-ttu-id="13548-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="13548-239">String</span><span class="sxs-lookup"><span data-stu-id="13548-239">String</span></span>|  
|<span data-ttu-id="13548-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="13548-240">IS_NULLABLE</span></span>|<span data-ttu-id="13548-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-241">Boolean</span></span>|  
|<span data-ttu-id="13548-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-242">DATA_TYPE</span></span>|<span data-ttu-id="13548-243">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-243">Int32</span></span>|  
|<span data-ttu-id="13548-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="13548-245">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-245">Int64</span></span>|  
|<span data-ttu-id="13548-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="13548-247">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-247">Int64</span></span>|  
|<span data-ttu-id="13548-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="13548-249">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-249">Int32</span></span>|  
|<span data-ttu-id="13548-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="13548-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="13548-251">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-251">Int16</span></span>|  
|<span data-ttu-id="13548-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-252">DESCRIPTION</span></span>|<span data-ttu-id="13548-253">String</span><span class="sxs-lookup"><span data-stu-id="13548-253">String</span></span>|  
|<span data-ttu-id="13548-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-254">TYPE_NAME</span></span>|<span data-ttu-id="13548-255">String</span><span class="sxs-lookup"><span data-stu-id="13548-255">String</span></span>|  
|<span data-ttu-id="13548-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="13548-257">String</span><span class="sxs-lookup"><span data-stu-id="13548-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="13548-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="13548-258">Catalog</span></span>  
  
|<span data-ttu-id="13548-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-259">ColumnName</span></span>|<span data-ttu-id="13548-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-261">CATALOG_NAME</span></span>|<span data-ttu-id="13548-262">String</span><span class="sxs-lookup"><span data-stu-id="13548-262">String</span></span>|  
|<span data-ttu-id="13548-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-263">DESCRIPTION</span></span>|<span data-ttu-id="13548-264">String</span><span class="sxs-lookup"><span data-stu-id="13548-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="13548-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-265">Indexes</span></span>  
  
|<span data-ttu-id="13548-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-266">ColumnName</span></span>|<span data-ttu-id="13548-267">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-268">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-269">String</span><span class="sxs-lookup"><span data-stu-id="13548-269">String</span></span>|  
|<span data-ttu-id="13548-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-271">String</span><span class="sxs-lookup"><span data-stu-id="13548-271">String</span></span>|  
|<span data-ttu-id="13548-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-272">TABLE_NAME</span></span>|<span data-ttu-id="13548-273">String</span><span class="sxs-lookup"><span data-stu-id="13548-273">String</span></span>|  
|<span data-ttu-id="13548-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-274">INDEX_CATALOG</span></span>|<span data-ttu-id="13548-275">String</span><span class="sxs-lookup"><span data-stu-id="13548-275">String</span></span>|  
|<span data-ttu-id="13548-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="13548-277">String</span><span class="sxs-lookup"><span data-stu-id="13548-277">String</span></span>|  
|<span data-ttu-id="13548-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-278">INDEX_NAME</span></span>|<span data-ttu-id="13548-279">String</span><span class="sxs-lookup"><span data-stu-id="13548-279">String</span></span>|  
|<span data-ttu-id="13548-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="13548-280">PRIMARY_KEY</span></span>|<span data-ttu-id="13548-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-281">Boolean</span></span>|  
|<span data-ttu-id="13548-282">JEDINEČNÝ</span><span class="sxs-lookup"><span data-stu-id="13548-282">UNIQUE</span></span>|<span data-ttu-id="13548-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-283">Boolean</span></span>|  
|<span data-ttu-id="13548-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="13548-284">CLUSTERED</span></span>|<span data-ttu-id="13548-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-285">Boolean</span></span>|  
|<span data-ttu-id="13548-286">TYP</span><span class="sxs-lookup"><span data-stu-id="13548-286">TYPE</span></span>|<span data-ttu-id="13548-287">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-287">Int32</span></span>|  
|<span data-ttu-id="13548-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="13548-288">FILL_FACTOR</span></span>|<span data-ttu-id="13548-289">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-289">Int32</span></span>|  
|<span data-ttu-id="13548-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="13548-290">INITIAL_SIZE</span></span>|<span data-ttu-id="13548-291">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-291">Int32</span></span>|  
|<span data-ttu-id="13548-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="13548-292">NULLS</span></span>|<span data-ttu-id="13548-293">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-293">Int32</span></span>|  
|<span data-ttu-id="13548-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="13548-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="13548-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-295">Boolean</span></span>|  
|<span data-ttu-id="13548-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="13548-296">AUTO_UPDATE</span></span>|<span data-ttu-id="13548-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-297">Boolean</span></span>|  
|<span data-ttu-id="13548-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="13548-298">NULL_COLLATION</span></span>|<span data-ttu-id="13548-299">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-299">Int32</span></span>|  
|<span data-ttu-id="13548-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-301">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-301">Int64</span></span>|  
|<span data-ttu-id="13548-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-302">COLUMN_NAME</span></span>|<span data-ttu-id="13548-303">String</span><span class="sxs-lookup"><span data-stu-id="13548-303">String</span></span>|  
|<span data-ttu-id="13548-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-304">COLUMN_GUID</span></span>|<span data-ttu-id="13548-305">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-305">Guid</span></span>|  
|<span data-ttu-id="13548-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-306">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-307">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-307">Int64</span></span>|  
|<span data-ttu-id="13548-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="13548-308">COLLATION</span></span>|<span data-ttu-id="13548-309">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-309">Int16</span></span>|  
|<span data-ttu-id="13548-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="13548-310">CARDINALITY</span></span>|<span data-ttu-id="13548-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="13548-311">Decimal</span></span>|  
|<span data-ttu-id="13548-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="13548-312">PAGES</span></span>|<span data-ttu-id="13548-313">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-313">Int32</span></span>|  
|<span data-ttu-id="13548-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="13548-314">FILTER_CONDITION</span></span>|<span data-ttu-id="13548-315">String</span><span class="sxs-lookup"><span data-stu-id="13548-315">String</span></span>|  
|<span data-ttu-id="13548-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="13548-316">INTEGRATED</span></span>|<span data-ttu-id="13548-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="13548-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="13548-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="13548-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="13548-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="13548-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-320">Tables</span></span>  
  
-   <span data-ttu-id="13548-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-321">Columns</span></span>  
  
-   <span data-ttu-id="13548-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-322">Procedures</span></span>  
  
-   <span data-ttu-id="13548-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="13548-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="13548-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="13548-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="13548-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="13548-325">Views</span></span>  
  
-   <span data-ttu-id="13548-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="13548-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-327">Tables</span></span>  
  
|<span data-ttu-id="13548-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-328">ColumnName</span></span>|<span data-ttu-id="13548-329">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-330">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-331">String</span><span class="sxs-lookup"><span data-stu-id="13548-331">String</span></span>|  
|<span data-ttu-id="13548-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-333">String</span><span class="sxs-lookup"><span data-stu-id="13548-333">String</span></span>|  
|<span data-ttu-id="13548-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-334">TABLE_NAME</span></span>|<span data-ttu-id="13548-335">String</span><span class="sxs-lookup"><span data-stu-id="13548-335">String</span></span>|  
|<span data-ttu-id="13548-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-336">TABLE_TYPE</span></span>|<span data-ttu-id="13548-337">String</span><span class="sxs-lookup"><span data-stu-id="13548-337">String</span></span>|  
|<span data-ttu-id="13548-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-338">TABLE_GUID</span></span>|<span data-ttu-id="13548-339">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-339">Guid</span></span>|  
|<span data-ttu-id="13548-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-340">DESCRIPTION</span></span>|<span data-ttu-id="13548-341">String</span><span class="sxs-lookup"><span data-stu-id="13548-341">String</span></span>|  
|<span data-ttu-id="13548-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-342">TABLE_PROPID</span></span>|<span data-ttu-id="13548-343">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-343">Int64</span></span>|  
|<span data-ttu-id="13548-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-344">DATE_CREATED</span></span>|<span data-ttu-id="13548-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-345">DateTime</span></span>|  
|<span data-ttu-id="13548-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-346">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="13548-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-348">Columns</span></span>  
  
|<span data-ttu-id="13548-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-349">ColumnName</span></span>|<span data-ttu-id="13548-350">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-351">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-352">String</span><span class="sxs-lookup"><span data-stu-id="13548-352">String</span></span>|  
|<span data-ttu-id="13548-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-354">String</span><span class="sxs-lookup"><span data-stu-id="13548-354">String</span></span>|  
|<span data-ttu-id="13548-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-355">TABLE_NAME</span></span>|<span data-ttu-id="13548-356">String</span><span class="sxs-lookup"><span data-stu-id="13548-356">String</span></span>|  
|<span data-ttu-id="13548-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-357">COLUMN_NAME</span></span>|<span data-ttu-id="13548-358">String</span><span class="sxs-lookup"><span data-stu-id="13548-358">String</span></span>|  
|<span data-ttu-id="13548-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-359">COLUMN_GUID</span></span>|<span data-ttu-id="13548-360">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-360">Guid</span></span>|  
|<span data-ttu-id="13548-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-361">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-362">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-362">Int64</span></span>|  
|<span data-ttu-id="13548-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-364">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-364">Int64</span></span>|  
|<span data-ttu-id="13548-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="13548-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-366">Boolean</span></span>|  
|<span data-ttu-id="13548-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="13548-368">String</span><span class="sxs-lookup"><span data-stu-id="13548-368">String</span></span>|  
|<span data-ttu-id="13548-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="13548-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="13548-370">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-370">Int64</span></span>|  
|<span data-ttu-id="13548-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="13548-371">IS_NULLABLE</span></span>|<span data-ttu-id="13548-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-372">Boolean</span></span>|  
|<span data-ttu-id="13548-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-373">DATA_TYPE</span></span>|<span data-ttu-id="13548-374">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-374">Int32</span></span>|  
|<span data-ttu-id="13548-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-375">TYPE_GUID</span></span>|<span data-ttu-id="13548-376">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-376">Guid</span></span>|  
|<span data-ttu-id="13548-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="13548-378">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-378">Int64</span></span>|  
|<span data-ttu-id="13548-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="13548-380">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-380">Int64</span></span>|  
|<span data-ttu-id="13548-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="13548-382">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-382">Int32</span></span>|  
|<span data-ttu-id="13548-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="13548-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="13548-384">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-384">Int16</span></span>|  
|<span data-ttu-id="13548-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="13548-386">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-386">Int64</span></span>|  
|<span data-ttu-id="13548-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="13548-388">String</span><span class="sxs-lookup"><span data-stu-id="13548-388">String</span></span>|  
|<span data-ttu-id="13548-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="13548-390">String</span><span class="sxs-lookup"><span data-stu-id="13548-390">String</span></span>|  
|<span data-ttu-id="13548-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="13548-392">String</span><span class="sxs-lookup"><span data-stu-id="13548-392">String</span></span>|  
|<span data-ttu-id="13548-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="13548-394">String</span><span class="sxs-lookup"><span data-stu-id="13548-394">String</span></span>|  
|<span data-ttu-id="13548-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="13548-396">String</span><span class="sxs-lookup"><span data-stu-id="13548-396">String</span></span>|  
|<span data-ttu-id="13548-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-397">COLLATION_NAME</span></span>|<span data-ttu-id="13548-398">String</span><span class="sxs-lookup"><span data-stu-id="13548-398">String</span></span>|  
|<span data-ttu-id="13548-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="13548-400">String</span><span class="sxs-lookup"><span data-stu-id="13548-400">String</span></span>|  
|<span data-ttu-id="13548-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="13548-402">String</span><span class="sxs-lookup"><span data-stu-id="13548-402">String</span></span>|  
|<span data-ttu-id="13548-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-403">DOMAIN_NAME</span></span>|<span data-ttu-id="13548-404">String</span><span class="sxs-lookup"><span data-stu-id="13548-404">String</span></span>|  
|<span data-ttu-id="13548-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-405">DESCRIPTION</span></span>|<span data-ttu-id="13548-406">String</span><span class="sxs-lookup"><span data-stu-id="13548-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="13548-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-407">Procedures</span></span>  
  
|<span data-ttu-id="13548-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-408">ColumnName</span></span>|<span data-ttu-id="13548-409">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="13548-411">String</span><span class="sxs-lookup"><span data-stu-id="13548-411">String</span></span>|  
|<span data-ttu-id="13548-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="13548-413">String</span><span class="sxs-lookup"><span data-stu-id="13548-413">String</span></span>|  
|<span data-ttu-id="13548-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="13548-415">String</span><span class="sxs-lookup"><span data-stu-id="13548-415">String</span></span>|  
|<span data-ttu-id="13548-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="13548-417">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-417">Int16</span></span>|  
|<span data-ttu-id="13548-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="13548-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="13548-419">String</span><span class="sxs-lookup"><span data-stu-id="13548-419">String</span></span>|  
|<span data-ttu-id="13548-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-420">DESCRIPTION</span></span>|<span data-ttu-id="13548-421">String</span><span class="sxs-lookup"><span data-stu-id="13548-421">String</span></span>|  
|<span data-ttu-id="13548-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-422">DATE_CREATED</span></span>|<span data-ttu-id="13548-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-423">DateTime</span></span>|  
|<span data-ttu-id="13548-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-424">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="13548-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="13548-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="13548-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-427">ColumnName</span></span>|<span data-ttu-id="13548-428">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="13548-430">String</span><span class="sxs-lookup"><span data-stu-id="13548-430">String</span></span>|  
|<span data-ttu-id="13548-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="13548-432">String</span><span class="sxs-lookup"><span data-stu-id="13548-432">String</span></span>|  
|<span data-ttu-id="13548-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="13548-434">String</span><span class="sxs-lookup"><span data-stu-id="13548-434">String</span></span>|  
|<span data-ttu-id="13548-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-435">COLUMN_NAME</span></span>|<span data-ttu-id="13548-436">String</span><span class="sxs-lookup"><span data-stu-id="13548-436">String</span></span>|  
|<span data-ttu-id="13548-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-437">COLUMN_GUID</span></span>|<span data-ttu-id="13548-438">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-438">Guid</span></span>|  
|<span data-ttu-id="13548-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-439">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-440">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-440">Int64</span></span>|  
|<span data-ttu-id="13548-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="13548-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="13548-442">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-442">Int64</span></span>|  
|<span data-ttu-id="13548-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-444">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-444">Int64</span></span>|  
|<span data-ttu-id="13548-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="13548-445">IS_NULLABLE</span></span>|<span data-ttu-id="13548-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-446">Boolean</span></span>|  
|<span data-ttu-id="13548-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-447">DATA_TYPE</span></span>|<span data-ttu-id="13548-448">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-448">Int32</span></span>|  
|<span data-ttu-id="13548-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-449">TYPE_GUID</span></span>|<span data-ttu-id="13548-450">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-450">Guid</span></span>|  
|<span data-ttu-id="13548-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="13548-452">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-452">Int64</span></span>|  
|<span data-ttu-id="13548-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="13548-454">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-454">Int64</span></span>|  
|<span data-ttu-id="13548-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="13548-456">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-456">Int32</span></span>|  
|<span data-ttu-id="13548-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="13548-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="13548-458">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-458">Int16</span></span>|  
|<span data-ttu-id="13548-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-459">DESCRIPTION</span></span>|<span data-ttu-id="13548-460">String</span><span class="sxs-lookup"><span data-stu-id="13548-460">String</span></span>|  
|<span data-ttu-id="13548-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="13548-461">OVERLOAD</span></span>|<span data-ttu-id="13548-462">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="13548-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="13548-463">Views</span></span>  
  
|<span data-ttu-id="13548-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-464">ColumnName</span></span>|<span data-ttu-id="13548-465">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-466">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-467">String</span><span class="sxs-lookup"><span data-stu-id="13548-467">String</span></span>|  
|<span data-ttu-id="13548-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-469">String</span><span class="sxs-lookup"><span data-stu-id="13548-469">String</span></span>|  
|<span data-ttu-id="13548-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-470">TABLE_NAME</span></span>|<span data-ttu-id="13548-471">String</span><span class="sxs-lookup"><span data-stu-id="13548-471">String</span></span>|  
|<span data-ttu-id="13548-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="13548-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="13548-473">String</span><span class="sxs-lookup"><span data-stu-id="13548-473">String</span></span>|  
|<span data-ttu-id="13548-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="13548-474">CHECK_OPTION</span></span>|<span data-ttu-id="13548-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-475">Boolean</span></span>|  
|<span data-ttu-id="13548-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="13548-476">IS_UPDATABLE</span></span>|<span data-ttu-id="13548-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-477">Boolean</span></span>|  
|<span data-ttu-id="13548-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-478">DESCRIPTION</span></span>|<span data-ttu-id="13548-479">String</span><span class="sxs-lookup"><span data-stu-id="13548-479">String</span></span>|  
|<span data-ttu-id="13548-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-480">DATE_CREATED</span></span>|<span data-ttu-id="13548-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-481">DateTime</span></span>|  
|<span data-ttu-id="13548-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-482">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="13548-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-484">Indexes</span></span>  
  
|<span data-ttu-id="13548-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-485">ColumnName</span></span>|<span data-ttu-id="13548-486">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-487">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-488">String</span><span class="sxs-lookup"><span data-stu-id="13548-488">String</span></span>|  
|<span data-ttu-id="13548-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-490">String</span><span class="sxs-lookup"><span data-stu-id="13548-490">String</span></span>|  
|<span data-ttu-id="13548-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-491">TABLE_NAME</span></span>|<span data-ttu-id="13548-492">String</span><span class="sxs-lookup"><span data-stu-id="13548-492">String</span></span>|  
|<span data-ttu-id="13548-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-493">INDEX_CATALOG</span></span>|<span data-ttu-id="13548-494">String</span><span class="sxs-lookup"><span data-stu-id="13548-494">String</span></span>|  
|<span data-ttu-id="13548-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="13548-496">String</span><span class="sxs-lookup"><span data-stu-id="13548-496">String</span></span>|  
|<span data-ttu-id="13548-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-497">INDEX_NAME</span></span>|<span data-ttu-id="13548-498">String</span><span class="sxs-lookup"><span data-stu-id="13548-498">String</span></span>|  
|<span data-ttu-id="13548-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="13548-499">PRIMARY_KEY</span></span>|<span data-ttu-id="13548-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-500">Boolean</span></span>|  
|<span data-ttu-id="13548-501">JEDINEČNÝ</span><span class="sxs-lookup"><span data-stu-id="13548-501">UNIQUE</span></span>|<span data-ttu-id="13548-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-502">Boolean</span></span>|  
|<span data-ttu-id="13548-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="13548-503">CLUSTERED</span></span>|<span data-ttu-id="13548-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-504">Boolean</span></span>|  
|<span data-ttu-id="13548-505">TYP</span><span class="sxs-lookup"><span data-stu-id="13548-505">TYPE</span></span>|<span data-ttu-id="13548-506">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-506">Int32</span></span>|  
|<span data-ttu-id="13548-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="13548-507">FILL_FACTOR</span></span>|<span data-ttu-id="13548-508">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-508">Int32</span></span>|  
|<span data-ttu-id="13548-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="13548-509">INITIAL_SIZE</span></span>|<span data-ttu-id="13548-510">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-510">Int32</span></span>|  
|<span data-ttu-id="13548-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="13548-511">NULLS</span></span>|<span data-ttu-id="13548-512">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-512">Int32</span></span>|  
|<span data-ttu-id="13548-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="13548-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="13548-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-514">Boolean</span></span>|  
|<span data-ttu-id="13548-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="13548-515">AUTO_UPDATE</span></span>|<span data-ttu-id="13548-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-516">Boolean</span></span>|  
|<span data-ttu-id="13548-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="13548-517">NULL_COLLATION</span></span>|<span data-ttu-id="13548-518">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-518">Int32</span></span>|  
|<span data-ttu-id="13548-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-520">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-520">Int64</span></span>|  
|<span data-ttu-id="13548-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-521">COLUMN_NAME</span></span>|<span data-ttu-id="13548-522">String</span><span class="sxs-lookup"><span data-stu-id="13548-522">String</span></span>|  
|<span data-ttu-id="13548-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-523">COLUMN_GUID</span></span>|<span data-ttu-id="13548-524">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-524">Guid</span></span>|  
|<span data-ttu-id="13548-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-525">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-526">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-526">Int64</span></span>|  
|<span data-ttu-id="13548-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="13548-527">COLLATION</span></span>|<span data-ttu-id="13548-528">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-528">Int16</span></span>|  
|<span data-ttu-id="13548-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="13548-529">CARDINALITY</span></span>|<span data-ttu-id="13548-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="13548-530">Decimal</span></span>|  
|<span data-ttu-id="13548-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="13548-531">PAGES</span></span>|<span data-ttu-id="13548-532">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-532">Int32</span></span>|  
|<span data-ttu-id="13548-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="13548-533">FILTER_CONDITION</span></span>|<span data-ttu-id="13548-534">String</span><span class="sxs-lookup"><span data-stu-id="13548-534">String</span></span>|  
|<span data-ttu-id="13548-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="13548-535">INTEGRATED</span></span>|<span data-ttu-id="13548-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="13548-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="13548-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="13548-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="13548-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="13548-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-539">Tables</span></span>  
  
-   <span data-ttu-id="13548-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-540">Columns</span></span>  
  
-   <span data-ttu-id="13548-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-541">Procedures</span></span>  
  
-   <span data-ttu-id="13548-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="13548-542">Views</span></span>  
  
-   <span data-ttu-id="13548-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="13548-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="13548-544">Tables</span></span>  
  
|<span data-ttu-id="13548-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-545">ColumnName</span></span>|<span data-ttu-id="13548-546">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-547">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-548">String</span><span class="sxs-lookup"><span data-stu-id="13548-548">String</span></span>|  
|<span data-ttu-id="13548-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-550">String</span><span class="sxs-lookup"><span data-stu-id="13548-550">String</span></span>|  
|<span data-ttu-id="13548-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-551">TABLE_NAME</span></span>|<span data-ttu-id="13548-552">String</span><span class="sxs-lookup"><span data-stu-id="13548-552">String</span></span>|  
|<span data-ttu-id="13548-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-553">TABLE_TYPE</span></span>|<span data-ttu-id="13548-554">String</span><span class="sxs-lookup"><span data-stu-id="13548-554">String</span></span>|  
|<span data-ttu-id="13548-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-555">TABLE_GUID</span></span>|<span data-ttu-id="13548-556">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-556">Guid</span></span>|  
|<span data-ttu-id="13548-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-557">DESCRIPTION</span></span>|<span data-ttu-id="13548-558">String</span><span class="sxs-lookup"><span data-stu-id="13548-558">String</span></span>|  
|<span data-ttu-id="13548-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-559">TABLE_PROPID</span></span>|<span data-ttu-id="13548-560">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-560">Int64</span></span>|  
|<span data-ttu-id="13548-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-561">DATE_CREATED</span></span>|<span data-ttu-id="13548-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-562">DateTime</span></span>|  
|<span data-ttu-id="13548-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-563">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="13548-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="13548-565">Columns</span></span>  
  
|<span data-ttu-id="13548-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-566">ColumnName</span></span>|<span data-ttu-id="13548-567">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-568">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-569">String</span><span class="sxs-lookup"><span data-stu-id="13548-569">String</span></span>|  
|<span data-ttu-id="13548-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-571">String</span><span class="sxs-lookup"><span data-stu-id="13548-571">String</span></span>|  
|<span data-ttu-id="13548-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-572">TABLE_NAME</span></span>|<span data-ttu-id="13548-573">String</span><span class="sxs-lookup"><span data-stu-id="13548-573">String</span></span>|  
|<span data-ttu-id="13548-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-574">COLUMN_NAME</span></span>|<span data-ttu-id="13548-575">String</span><span class="sxs-lookup"><span data-stu-id="13548-575">String</span></span>|  
|<span data-ttu-id="13548-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-576">COLUMN_GUID</span></span>|<span data-ttu-id="13548-577">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-577">Guid</span></span>|  
|<span data-ttu-id="13548-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-578">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-579">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-579">Int64</span></span>|  
|<span data-ttu-id="13548-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-581">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-581">Int64</span></span>|  
|<span data-ttu-id="13548-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="13548-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-583">Boolean</span></span>|  
|<span data-ttu-id="13548-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="13548-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="13548-585">String</span><span class="sxs-lookup"><span data-stu-id="13548-585">String</span></span>|  
|<span data-ttu-id="13548-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="13548-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="13548-587">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-587">Int64</span></span>|  
|<span data-ttu-id="13548-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="13548-588">IS_NULLABLE</span></span>|<span data-ttu-id="13548-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-589">Boolean</span></span>|  
|<span data-ttu-id="13548-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-590">DATA_TYPE</span></span>|<span data-ttu-id="13548-591">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-591">Int32</span></span>|  
|<span data-ttu-id="13548-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-592">TYPE_GUID</span></span>|<span data-ttu-id="13548-593">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-593">Guid</span></span>|  
|<span data-ttu-id="13548-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="13548-595">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-595">Int64</span></span>|  
|<span data-ttu-id="13548-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="13548-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="13548-597">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-597">Int64</span></span>|  
|<span data-ttu-id="13548-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="13548-599">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-599">Int32</span></span>|  
|<span data-ttu-id="13548-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="13548-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="13548-601">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-601">Int16</span></span>|  
|<span data-ttu-id="13548-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="13548-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="13548-603">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-603">Int64</span></span>|  
|<span data-ttu-id="13548-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="13548-605">String</span><span class="sxs-lookup"><span data-stu-id="13548-605">String</span></span>|  
|<span data-ttu-id="13548-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="13548-607">String</span><span class="sxs-lookup"><span data-stu-id="13548-607">String</span></span>|  
|<span data-ttu-id="13548-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="13548-609">String</span><span class="sxs-lookup"><span data-stu-id="13548-609">String</span></span>|  
|<span data-ttu-id="13548-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="13548-611">String</span><span class="sxs-lookup"><span data-stu-id="13548-611">String</span></span>|  
|<span data-ttu-id="13548-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="13548-613">String</span><span class="sxs-lookup"><span data-stu-id="13548-613">String</span></span>|  
|<span data-ttu-id="13548-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-614">COLLATION_NAME</span></span>|<span data-ttu-id="13548-615">String</span><span class="sxs-lookup"><span data-stu-id="13548-615">String</span></span>|  
|<span data-ttu-id="13548-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="13548-617">String</span><span class="sxs-lookup"><span data-stu-id="13548-617">String</span></span>|  
|<span data-ttu-id="13548-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="13548-619">String</span><span class="sxs-lookup"><span data-stu-id="13548-619">String</span></span>|  
|<span data-ttu-id="13548-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-620">DOMAIN_NAME</span></span>|<span data-ttu-id="13548-621">String</span><span class="sxs-lookup"><span data-stu-id="13548-621">String</span></span>|  
|<span data-ttu-id="13548-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-622">DESCRIPTION</span></span>|<span data-ttu-id="13548-623">String</span><span class="sxs-lookup"><span data-stu-id="13548-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="13548-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="13548-624">Procedures</span></span>  
  
|<span data-ttu-id="13548-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-625">ColumnName</span></span>|<span data-ttu-id="13548-626">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="13548-628">String</span><span class="sxs-lookup"><span data-stu-id="13548-628">String</span></span>|  
|<span data-ttu-id="13548-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="13548-630">String</span><span class="sxs-lookup"><span data-stu-id="13548-630">String</span></span>|  
|<span data-ttu-id="13548-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="13548-632">String</span><span class="sxs-lookup"><span data-stu-id="13548-632">String</span></span>|  
|<span data-ttu-id="13548-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="13548-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="13548-634">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-634">Int16</span></span>|  
|<span data-ttu-id="13548-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="13548-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="13548-636">String</span><span class="sxs-lookup"><span data-stu-id="13548-636">String</span></span>|  
|<span data-ttu-id="13548-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-637">DESCRIPTION</span></span>|<span data-ttu-id="13548-638">String</span><span class="sxs-lookup"><span data-stu-id="13548-638">String</span></span>|  
|<span data-ttu-id="13548-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-639">DATE_CREATED</span></span>|<span data-ttu-id="13548-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-640">DateTime</span></span>|  
|<span data-ttu-id="13548-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-641">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="13548-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="13548-643">Views</span></span>  
  
|<span data-ttu-id="13548-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-644">ColumnName</span></span>|<span data-ttu-id="13548-645">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-646">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-647">String</span><span class="sxs-lookup"><span data-stu-id="13548-647">String</span></span>|  
|<span data-ttu-id="13548-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-649">String</span><span class="sxs-lookup"><span data-stu-id="13548-649">String</span></span>|  
|<span data-ttu-id="13548-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-650">TABLE_NAME</span></span>|<span data-ttu-id="13548-651">String</span><span class="sxs-lookup"><span data-stu-id="13548-651">String</span></span>|  
|<span data-ttu-id="13548-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="13548-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="13548-653">String</span><span class="sxs-lookup"><span data-stu-id="13548-653">String</span></span>|  
|<span data-ttu-id="13548-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="13548-654">CHECK_OPTION</span></span>|<span data-ttu-id="13548-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-655">Boolean</span></span>|  
|<span data-ttu-id="13548-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="13548-656">IS_UPDATABLE</span></span>|<span data-ttu-id="13548-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-657">Boolean</span></span>|  
|<span data-ttu-id="13548-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="13548-658">DESCRIPTION</span></span>|<span data-ttu-id="13548-659">String</span><span class="sxs-lookup"><span data-stu-id="13548-659">String</span></span>|  
|<span data-ttu-id="13548-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="13548-660">DATE_CREATED</span></span>|<span data-ttu-id="13548-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-661">DateTime</span></span>|  
|<span data-ttu-id="13548-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="13548-662">DATE_MODIFIED</span></span>|<span data-ttu-id="13548-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="13548-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="13548-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="13548-664">Indexes</span></span>  
  
|<span data-ttu-id="13548-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="13548-665">ColumnName</span></span>|<span data-ttu-id="13548-666">Datový typ</span><span class="sxs-lookup"><span data-stu-id="13548-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="13548-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-667">TABLE_CATALOG</span></span>|<span data-ttu-id="13548-668">String</span><span class="sxs-lookup"><span data-stu-id="13548-668">String</span></span>|  
|<span data-ttu-id="13548-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="13548-670">String</span><span class="sxs-lookup"><span data-stu-id="13548-670">String</span></span>|  
|<span data-ttu-id="13548-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-671">TABLE_NAME</span></span>|<span data-ttu-id="13548-672">String</span><span class="sxs-lookup"><span data-stu-id="13548-672">String</span></span>|  
|<span data-ttu-id="13548-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="13548-673">INDEX_CATALOG</span></span>|<span data-ttu-id="13548-674">String</span><span class="sxs-lookup"><span data-stu-id="13548-674">String</span></span>|  
|<span data-ttu-id="13548-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="13548-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="13548-676">String</span><span class="sxs-lookup"><span data-stu-id="13548-676">String</span></span>|  
|<span data-ttu-id="13548-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-677">INDEX_NAME</span></span>|<span data-ttu-id="13548-678">String</span><span class="sxs-lookup"><span data-stu-id="13548-678">String</span></span>|  
|<span data-ttu-id="13548-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="13548-679">PRIMARY_KEY</span></span>|<span data-ttu-id="13548-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-680">Boolean</span></span>|  
|<span data-ttu-id="13548-681">JEDINEČNÝ</span><span class="sxs-lookup"><span data-stu-id="13548-681">UNIQUE</span></span>|<span data-ttu-id="13548-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-682">Boolean</span></span>|  
|<span data-ttu-id="13548-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="13548-683">CLUSTERED</span></span>|<span data-ttu-id="13548-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-684">Boolean</span></span>|  
|<span data-ttu-id="13548-685">TYP</span><span class="sxs-lookup"><span data-stu-id="13548-685">TYPE</span></span>|<span data-ttu-id="13548-686">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-686">Int32</span></span>|  
|<span data-ttu-id="13548-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="13548-687">FILL_FACTOR</span></span>|<span data-ttu-id="13548-688">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-688">Int32</span></span>|  
|<span data-ttu-id="13548-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="13548-689">INITIAL_SIZE</span></span>|<span data-ttu-id="13548-690">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-690">Int32</span></span>|  
|<span data-ttu-id="13548-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="13548-691">NULLS</span></span>|<span data-ttu-id="13548-692">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-692">Int32</span></span>|  
|<span data-ttu-id="13548-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="13548-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="13548-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-694">Boolean</span></span>|  
|<span data-ttu-id="13548-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="13548-695">AUTO_UPDATE</span></span>|<span data-ttu-id="13548-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-696">Boolean</span></span>|  
|<span data-ttu-id="13548-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="13548-697">NULL_COLLATION</span></span>|<span data-ttu-id="13548-698">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-698">Int32</span></span>|  
|<span data-ttu-id="13548-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="13548-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="13548-700">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-700">Int64</span></span>|  
|<span data-ttu-id="13548-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="13548-701">COLUMN_NAME</span></span>|<span data-ttu-id="13548-702">String</span><span class="sxs-lookup"><span data-stu-id="13548-702">String</span></span>|  
|<span data-ttu-id="13548-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="13548-703">COLUMN_GUID</span></span>|<span data-ttu-id="13548-704">identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="13548-704">Guid</span></span>|  
|<span data-ttu-id="13548-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="13548-705">COLUMN_PROPID</span></span>|<span data-ttu-id="13548-706">Int64</span><span class="sxs-lookup"><span data-stu-id="13548-706">Int64</span></span>|  
|<span data-ttu-id="13548-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="13548-707">COLLATION</span></span>|<span data-ttu-id="13548-708">Int16</span><span class="sxs-lookup"><span data-stu-id="13548-708">Int16</span></span>|  
|<span data-ttu-id="13548-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="13548-709">CARDINALITY</span></span>|<span data-ttu-id="13548-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="13548-710">Decimal</span></span>|  
|<span data-ttu-id="13548-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="13548-711">PAGES</span></span>|<span data-ttu-id="13548-712">Int32</span><span class="sxs-lookup"><span data-stu-id="13548-712">Int32</span></span>|  
|<span data-ttu-id="13548-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="13548-713">FILTER_CONDITION</span></span>|<span data-ttu-id="13548-714">String</span><span class="sxs-lookup"><span data-stu-id="13548-714">String</span></span>|  
|<span data-ttu-id="13548-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="13548-715">INTEGRATED</span></span>|<span data-ttu-id="13548-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="13548-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13548-717">Viz také</span><span class="sxs-lookup"><span data-stu-id="13548-717">See Also</span></span>  
 [<span data-ttu-id="13548-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="13548-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
