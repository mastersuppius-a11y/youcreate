# Quick Start Guide

## Before You Use The App - Run This SQL!

Open Supabase SQL Editor and run:

```sql
-- Add question_id to videos table
DO $$
BEGIN
  IF NOT EXISTS (
    SELECT 1 FROM information_schema.columns
    WHERE table_name = 'videos' AND column_name = 'question_id'
  ) THEN
    ALTER TABLE videos ADD COLUMN question_id integer;
  END IF;
END $$;

-- Add used_in_video to new_questions table
DO $$
BEGIN
  IF NOT EXISTS (
    SELECT 1 FROM information_schema.columns
    WHERE table_name = 'new_questions' AND column_name = 'used_in_video'
  ) THEN
    ALTER TABLE new_questions ADD COLUMN used_in_video text DEFAULT null;
  END IF;
END $$;
```

## Then Create Storage Bucket

1. Go to Supabase Dashboard → Storage
2. Create new bucket: `videos`
3. Make it **PUBLIC**

## Deploy Edge Functions (Optional)

Using Supabase CLI:
```bash
supabase login
supabase link --project-ref hljcqhqzqnedmwhwddcu
supabase functions deploy generate-captions
supabase functions deploy render-video
```

## What's Ready to Use

✅ **Gemini API** - Script generation
✅ **ElevenLabs API** - Voice generation with your voice ID
✅ **Supabase** - Database connected
✅ **Frontend** - Complete UI with 4-step pipeline

## How to Use

1. Select Exam
2. Select Course
3. Click "Generate Script" - Creates script with Gemini
4. Click "Generate Voice Over" - Creates audio with ElevenLabs
5. Click "Generate Captions" - Creates timed captions
6. Click "Render Video" - (Placeholder until Python backend is built)

## What's Not Built Yet

❌ Python video renderer - Need to build this next

See `SETUP_INSTRUCTIONS.md` for detailed information.
See `ROADMAP.md` for complete project plan.
